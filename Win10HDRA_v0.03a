# Script "HDR Automation" Final v0.3
# In this script, I automate the switch of HDR mode for Windows 10
# By Bertrand Givord and ChatGPT (GPT 3.5)

# Check if VLC is running
$vlcRunning = Get-Process -Name "vlc" -ErrorAction SilentlyContinue

# If VLC is running, switch Windows to HDR mode
if ($vlcRunning) {
    # Check if Windows is already in HDR mode
    $hdrEnabled = (Get-ItemProperty -Path "HKCU:\Software\Microsoft\Windows\DWM" -Name "UseMachineCheck").UseMachineCheck

    if (-not $hdrEnabled) {
        # Enable Windows HDR mode
        Set-ItemProperty -Path "HKCU:\Software\Microsoft\Windows\DWM" -Name "UseMachineCheck" -Value 1
        Set-ItemProperty -Path "HKCU:\Software\Microsoft\Windows\DWM" -Name "UseLuminanceForNonODTCaptures" -Value 1

        # Restart Windows Explorer to apply the changes
        Stop-Process -Name "explorer" -Force
        Start-Process -Name "explorer"
    }
}
else {
    # Check if Windows is in HDR mode
    $hdrEnabled = (Get-ItemProperty -Path "HKCU:\Software\Microsoft\Windows\DWM" -Name "UseMachineCheck").UseMachineCheck

    if ($hdrEnabled) {
        # Disable Windows HDR mode
        Set-ItemProperty -Path "HKCU:\Software\Microsoft\Windows\DWM" -Name "UseMachineCheck" -Value 0
        Set-ItemProperty -Path "HKCU:\Software\Microsoft\Windows\DWM" -Name "UseLuminanceForNonODTCaptures" -Value 0

        # Restart Windows Explorer to apply the changes
        Stop-Process -Name "explorer" -Force
        Start-Process -Name "explorer"
    }
}
