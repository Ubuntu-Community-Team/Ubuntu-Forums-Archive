---
title: "Login screen black after Nvidia installation"
date: 2020-01-04
forum: Desktop Environments
---

### Post by marius22 on 2020-01-04
Hello, 

I tried to update from 16.04 to 18.04 lately and ran into similar problems as I am having now. I tried to solve it with a clean 18.04 Installation, but it did not help. 

The clean install with Nouveau driver does start correctly, but does not restart after suspending the computer. I read that this might be solved by using the Nvidia driver, I wanted to use anyway. After installing the computer did not start and I had to change to UEFI insecure boot and set boot options in /etc/default/grub to
> GRUB_CMDLINE_LINUX_DEFAULT= "nomodeset"

At this point the computer got stuck in the  loading screen at 
> 
Started user manager for UID 121 


I used the recovery mode to install lightdm and switched to lightdm it using 
> Sudo dpkg-reconfigure lightdm 

At this point the computer starts and hear the Ubuntu starting sound, but the screen is black. I can switch to tty and login. Checking the status of lightm using 
> Systemctl status lightdm 
Shows 
> 
&#9679; lightdm.service - Light Display Manager
   Loaded: loaded (/lib/systemd/system/lightdm.service; indirect; vendor preset: enabled)
   Active: active (running) since Sat 2020-01-04 13:47:57 CET; 43s ago
     Docs: man:lightdm(1)
  Process: 916 ExecStartPre=/bin/sh -c [ "$(basename $(cat /etc/X11/default-display-manager 2>/dev/null))" = "lightdm" ] (code=exited, status=0/SUCCESS)
 Main PID: 921 (lightdm)
    Tasks: 13 (limit: 4915)
   CGroup: /system.slice/lightdm.service
           &#9500;&#9472;921 /usr/sbin/lightdm
           &#9492;&#9472;936 /usr/lib/xorg/Xorg -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch

Jan 04 13:47:57 DeepThought lightdm[979]: PAM unable to dlopen(pam_kwallet5.so): /lib/security/pam_kwallet5.so: cannot open shared object file: No such file or directory
Jan 04 13:47:57 DeepThought lightdm[979]: PAM adding faulty module: pam_kwallet5.so
Jan 04 13:47:57 DeepThought lightdm[979]: pam_unix(lightdm-greeter:session): session opened for user lightdm by (uid=0)
Jan 04 13:47:58 DeepThought lightdm[1126]: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Jan 04 13:47:58 DeepThought lightdm[1126]: PAM adding faulty module: pam_kwallet.so
Jan 04 13:47:58 DeepThought lightdm[1126]: PAM unable to dlopen(pam_kwallet5.so): /lib/security/pam_kwallet5.so: cannot open shared object file: No such file or directory
Jan 04 13:47:58 DeepThought lightdm[1126]: PAM adding faulty module: pam_kwallet5.so
Jan 04 13:47:58 DeepThought lightdm[1126]: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "marius"

Restarting lightdm does not work. I realised that I don't have a lightm.conf file at this point, so I created one with minimal Information:
> Greeter-session =lightdm-slick-greeter 
User-session = Ubuntu

I hope that is correct.

I can start my computer normally by purging the Nvidia driver and restaring the system, working with gdm3 and lightdm. 
The lightdm status is then similar but with additional line:
> lightdm[xxxx]: pam_unix(lightdm:session) : session opened for user marius by (uid=0) 
lightdm[yyyy]: Failed to write utmpx: No such file or directory

I tried with different versions of the Nvidia driver, same result. I am using an Inspiron 15 7000 with i5 processor and GeForce 940MX. 

Please let me know if you need more Information. It would be nice if you could explain some backgrounds for me to understand what is going on ( or just add some links).

Thanks,

Marius

---

### Post by Autodave on 2020-01-04
Where are you getting the drivers from?

---

### Post by marius22 on 2020-01-04
Hey thanks for your answer.

 I tried Software & Updates integrated in Ubuntu and the Nvidia ppa using the terminal. It does not make a difference.

---

### Post by Bashing-om on 2020-01-04
marius22; Welcome to the forum:)
 
> 
GRUB_CMDLINE_LINUX_DEFAULT= "nomodeset"


defeats Kernel Mode Setting, thus, the driver will not be able to load. Remove the boot parameter and reboot, Now what results ?

-my bit to try and help-

---

### Post by marius22 on 2020-01-05
Hello Bashing-om!

I tried without nomodeset, same problem. 

I add the boot.log , because there are some failes.  
```

grep -a FAILED boot.log 
[FAILED] Failed to start Create Static Device Nodes in /dev.
[FAILED] Failed to start Create Volatile Files and Directories.
[FAILED] Failed to start Network Time Synchronization.
[FAILED] Failed to start Network Name Resolution.
[FAILED] Failed to start Network Time Synchronization.
[FAILED] Failed to start Network Name Resolution.
[FAILED] Failed to start Network Name Resolution.
[FAILED] Failed to start Network Time Synchronization.
[FAILED] Failed to start Network Name Resolution.
[FAILED] Failed to start Network Time Synchronization.
[FAILED] Failed to start Network Name Resolution.
[FAILED] Failed to start Network Time Synchronization.
[FAILED] Failed to start Network Time Synchronization.
[FAILED] Failed to start Network Name Resolution.
[FAILED] Failed to start Avahi mDNS/DNS-SD Stack.
[FAILED] Failed to start Bluetooth service.
[FAILED] Failed to start Disk Manager.
[FAILED] Failed to start System Logging Service.
[FAILED] Failed to start Accounts Service.
[FAILED] Failed to start Dispatcher daemon for systemd-networkd.
[FAILED] Failed to start Create Volatile Files and Directories.
[FAILED] Failed to start Create Static Device Nodes in /dev.
[FAILED] Failed to start Create Volatile Files and Directories.
[FAILED] Failed to start Network Time Synchronization.
[FAILED] Failed to start Network Name Resolution.
[FAILED] Failed to start Network Time Synchronization.
[FAILED] Failed to start Network Name Resolution.
[FAILED] Failed to start Create Static Device Nodes in /dev.
[FAILED] Failed to start Create Volatile Files and Directories.
[FAILED] Failed to start Network Time Synchronization.
[FAILED] Failed to start Network Name Resolution.
[FAILED] Failed to start Network Time Synchronization.
[FAILED] Failed to start Network Name Resolution.
[FAILED] Failed to start Network Name Resolution.
[FAILED] Failed to start Network Time Synchronization.
[FAILED] Failed to start Network Time Synchronization.
[FAILED] Failed to start Network Name Resolution.
[FAILED] Failed to start Modem Manager.
[FAILED] Failed to start Avahi mDNS/DNS-SD Stack.
[FAILED] Failed to start Bluetooth service.
[FAILED] Failed to start NVIDIA Persistence Daemon.
[FAILED] Failed to start Dispatcher daemon for systemd-networkd.
[FAILED] Failed to start Accounts Service.
[FAILED] Failed to start System Logging Service.
[FAILED] Failed to start Disk Manager.
[FAILED] Failed to start Login Service.
[FAILED] Failed to start Thermal Daemon Service.
[FAILED] Failed to start WPA supplicant.
[FAILED] Failed to start Create Static Device Nodes in /dev.
[FAILED] Failed to start Create Volatile Files and Directories.
[FAILED] Failed to start Network Name Resolution.
[FAILED] Failed to start Network Time Synchronization.
[FAILED] Failed to start Create Static Device Nodes in /dev.
[FAILED] Failed to start Create Volatile Files and Directories.
[FAILED] Failed to start Network Name Resolution.
[FAILED] Failed to start Network Time Synchronization.
[FAILED] Failed to start Network Name Resolution.
[FAILED] Failed to start Network Time Synchronization.
[FAILED] Failed to start Network Name Resolution.
[FAILED] Failed to start Network Time Synchronization.
[FAILED] Failed to start Network Name Resolution.
[FAILED] Failed to start Network Name Resolution.
[FAILED] Failed to start Network Time Synchronization.
[FAILED] Failed to start Network Time Synchronization.
[FAILED] Failed to start Create Static Device Nodes in /dev.
[FAILED] Failed to start Create Volatile Files and Directories.
[FAILED] Failed to start Network Name Resolution.
[FAILED] Failed to start Network Time Synchronization.
[FAILED] Failed to start Network Name Resolution.
[FAILED] Failed to start Network Time Synchronization.
[FAILED] Failed to start Create Static Device Nodes in /dev.
[FAILED] Failed to start Create Volatile Files and Directories.
[FAILED] Failed to start Network Name Resolution.
[FAILED] Failed to start Network Time Synchronization.
[FAILED] Failed to start Network Name Resolution.
[FAILED] Failed to start Network Time Synchronization.
[FAILED] Failed to start Network Name Resolution.
[FAILED] Failed to start Network Name Resolution.
[FAILED] Failed to start Network Time Synchronization.
[FAILED] Failed to start Network Time Synchronization.
[FAILED] Failed to start Avahi mDNS/DNS-SD Stack.
[FAILED] Failed to start Dispatcher daemon for systemd-networkd.
[FAILED] Failed to start Disk Manager.
[FAILED] Failed to start System Logging Service.
[FAILED] Failed to start NVIDIA Persistence Daemon.
[FAILED] Failed to start Accounts Service.[/QUOTE]


However, these are the same FAILED as without the NVIDIA driver.  I noted that there is no log of an NVIDIA driver (except the NVIDIA persistance daemon, whatever that is )

> grep -a NVIDIA boot.log
         Starting NVIDIA Persistence Daemon...
[  OK  ] Started NVIDIA Persistence Daemon.
         Starting NVIDIA Persistence Daemon...
[FAILED] Failed to start NVIDIA Persistence Daemon.
         Starting NVIDIA Persistence Daemon...
         Starting NVIDIA Persistence Daemon...
[FAILED] Failed to start NVIDIA Persistence Daemon.

or does it have another name? 
here is the complete log if needed:

[QUOTE][  OK  ] Started Show Plymouth Boot Screen.
[  OK  ] Started Forward Password Requests to Plymouth Directory Watch.
[  OK  ] Reached target Local Encrypted Volumes.
[  OK  ] Started Tell Plymouth To Write Out Runtime Data.
[  OK  ] Started AppArmor initialization.
         Starting Raise network interfaces...
[  OK  ] Reached target System Initialization.
[  OK  ] Listening on ACPID Listen Socket.
[  OK  ] Started CUPS Scheduler.
         Starting Socket activation for snappy daemon.
[  OK  ] Started ACPI Events Check.
[  OK  ] Reached target Paths.
[  OK  ] Started Trigger anacron every hour.
[  OK  ] Started Daily apt download activities.
[  OK  ] Started Daily apt upgrade and clean activities.
[  OK  ] Listening on D-Bus System Message Bus Socket.
[  OK  ] Listening on UUID daemon activation socket.
[  OK  ] Started Daily Cleanup of Temporary Directories.
[  OK  ] Listening on CUPS Scheduler.
[  OK  ] Started Message of the Day.
[  OK  ] Started Discard unused blocks once a week.
[  OK  ] Reached target Timers.
[  OK  ] Listening on Avahi mDNS/DNS-SD Stack Activation Socket.
[  OK  ] Listening on Socket activation for snappy daemon.
[  OK  ] Reached target Sockets.
[  OK  ] Reached target Basic System.
         Starting LSB: automatic crash report generation...
[  OK  ] Reached target Login Prompts.
         Starting Thermal Daemon Service...
         Starting Detect the available GPUs and deal with any system changes...
         Starting System Logging Service...
[  OK  ] Started Run anacron jobs.
         Starting Disk Manager...
         Starting Accounts Service...
[  OK  ] Started D-Bus System Message Bus.
         Starting Network Manager...
         Starting WPA supplicant...
         Starting Login Service...
         Starting LSB: Record successful boot for GRUB...
         Starting LSB: Speech Dispatcher...
[  OK  ] Started Regular background program processing daemon.
[  OK  ] Started irqbalance daemon.
         Starting Modem Manager...
[  OK  ] Started ACPI event daemon.
[  OK  ] Started CUPS Scheduler.
         Starting Bluetooth service...
         Starting Avahi mDNS/DNS-SD Stack...
         Starting Save/Restore Sound Card State...
         Starting Dispatcher daemon for systemd-networkd...
[  OK  ] Started Set the CPU Frequency Scaling governor.
         Starting Restore /etc/resolv.conf if the system crashed before the ppp link was shut down...
         Starting Snappy daemon...
[  OK  ] Started System Logging Service.
[  OK  ] Started Raise network interfaces.
[  OK  ] Started Detect the available GPUs and deal with any system changes.
[  OK  ] Started Restore /etc/resolv.conf if the system crashed before the ppp link was shut down.
[  OK  ] Started Save/Restore Sound Card State.
[  OK  ] Started Thermal Daemon Service.
[  OK  ] Reached target Sound Card.
[  OK  ] Started LSB: Speech Dispatcher.
[  OK  ] Started Avahi mDNS/DNS-SD Stack.
[  OK  ] Started Make remote CUPS printers available locally.
[  OK  ] Started LSB: automatic crash report generation.
[  OK  ] Started Bluetooth service.
[  OK  ] Reached target Bluetooth.
[  OK  ] Started WPA supplicant.
         Starting Authorization Manager...
[  OK  ] Started LSB: Record successful boot for GRUB.
         Starting Hostname Service...
[  OK  ] Started Authorization Manager.
[  OK  ] Started Accounts Service.
[  OK  ] Started Modem Manager.
[  OK  ] Started Dispatcher daemon for systemd-networkd.
[  OK  ] Started Hostname Service.
[  OK  ] Started Disk Manager.
[  OK  ] Started Login Service.
[  OK  ] Started Snappy daemon.
         Starting Wait until snapd is fully seeded...
[  OK  ] Started Network Manager.
[  OK  ] Reached target Network.
         Starting Permit User Sessions...
[  OK  ] Started Unattended Upgrades Shutdown.
         Starting Network Manager Wait Online...
         Starting Network Manager Script Dispatcher Service...
[  OK  ] Started Permit User Sessions.
         Starting GNOME Display Manager...
         Starting Hold until boot process finishes up...
[  OK  ] Started Network Manager Script Dispatcher Service.
[  OK  ] Started GNOME Display Manager.
         Starting NVIDIA Persistence Daemon...
[  OK  ] Started NVIDIA Persistence Daemon.
[  OK  ] Started Show Plymouth Boot Screen.
[  OK  ] Started Forward Password Requests to Plymouth Directory Watch.
[  OK  ] Reached target Local Encrypted Volumes.
[  OK  ] Mounted Mount unit for chromium, revision 971.
[  OK  ] Started Flush Journal to Persistent Storage.
[  OK  ] Mounted Mount unit for core18, revision 1288.
[  OK  ] Listening on Load/Save RF Kill Switch Status /dev/rfkill Watch.
         Starting Load/Save RF Kill Switch Status...
[  OK  ] Found device SAMSUNG_SSD_PM871b_M.2_2280_128GB 2.
         Mounting /mnt/sda...
         Starting Create Static Device Nodes in /dev...
[  OK  ] Started Load/Save RF Kill Switch Status.
[  OK  ] Mounted /mnt/sda.
[FAILED] Failed to start Create Static Device Nodes in /dev.
See 'systemctl status systemd-tmpfiles-setup-dev.service' for details.
[  OK  ] Found device SAMSUNG_SSD_PM871b_M.2&#8230;_128GB EFI\x20System\x20Partition.
         Starting File System Check on /dev/disk/by-uuid/F437-EF70...
[  OK  ] Started File System Check Daemon to report status.
[  OK  ] Started File System Check on /dev/disk/by-uuid/F437-EF70.
         Mounting /boot/efi...
[  OK  ] Mounted /boot/efi.
[  OK  ] Reached target Local File Systems.
         Starting Create Volatile Files and Directories...
         Starting Set console font and keymap...
         Starting AppArmor initialization...
         Starting Clean up any mess left by 0dns-up...
         Starting Tell Plymouth To Write Out Runtime Data...
[  OK  ] Started Set console font and keymap.
[FAILED] Failed to start Create Volatile Files and Directories.
See 'systemctl status systemd-tmpfiles-setup.service' for details.
         Starting Network Name Resolution...
         Starting Network Time Synchronization...
         Starting Update UTMP about System Boot/Shutdown...
[  OK  ] Started Clean up any mess left by 0dns-up.
[  OK  ] Started Update UTMP about System Boot/Shutdown.
[  OK  ] Created slice system-systemd\x2dbacklight.slice.
         Starting Load/Save Screen Backlight Brightness of backlight:intel_backlight...
         Starting Load/Save Screen Backlight Brightness of leds:dell::kbd_backlight...
[  OK  ] Started Load/Save Screen Backlight Brightness of leds:dell::kbd_backlight.
[  OK  ] Reached target Sound Card.
[FAILED] Failed to start Network Time Synchronization.
See 'systemctl status systemd-timesyncd.service' for details.
[  OK  ] Stopped Network Time Synchronization.
         Starting Network Time Synchronization...
[FAILED] Failed to start Network Name Resolution.
See 'systemctl status systemd-resolved.service' for details.
[  OK  ] Stopped Network Name Resolution.
         Starting Network Name Resolution...
[FAILED] Failed to start Network Time Synchronization.
See 'systemctl status systemd-timesyncd.service' for details.
[FAILED] Failed to start Network Name Resolution.
See 'systemctl status systemd-resolved.service' for details.
[  OK  ] Stopped Network Name Resolution.
         Starting Network Name Resolution...
[  OK  ] Stopped Network Time Synchronization.
         Starting Network Time Synchronization...
[FAILED] Failed to start Network Name Resolution.
See 'systemctl status systemd-resolved.service' for details.
[FAILED] Failed to start Network Time Synchronization.
See 'systemctl status systemd-timesyncd.service' for details.
[  OK  ] Stopped Network Time Synchronization.
         Starting Network Time Synchronization...
[  OK  ] Stopped Network Name Resolution.
         Starting Network Name Resolution...
[FAILED] Failed to start Network Name Resolution.
See 'systemctl status systemd-resolved.service' for details.
[  OK  ] Stopped Network Name Resolution.
         Starting Network Name Resolution...
[FAILED] Failed to start Network Time Synchronization.
See 'systemctl status systemd-timesyncd.service' for details.
[  OK  ] Stopped Network Time Synchronization.
         Starting Network Time Synchronization...
[FAILED] Failed to start Network Name Resolution.
See 'systemctl status systemd-resolved.service' for details.
[FAILED] Failed to start Network Time Synchronization.
See 'systemctl status systemd-timesyncd.service' for details.
[  OK  ] Stopped Network Time Synchronization.
[FAILED] Failed to start Network Time Synchronization.
See 'systemctl status systemd-timesyncd.service' for details.
[  OK  ] Stopped Network Name Resolution.
[FAILED] Failed to start Network Name Resolution.
See 'systemctl status systemd-resolved.service' for details.
[  OK  ] Reached target System Time Synchronized.
[  OK  ] Reached target Host and Network Name Lookups.
[  OK  ] Started Load/Save Screen Backlight Brightness of backlight:intel_backlight.
[  OK  ] Started Tell Plymouth To Write Out Runtime Data.
[  OK  ] Started AppArmor initialization.
[  OK  ] Reached target System Initialization.
[  OK  ] Started Discard unused blocks once a week.
[  OK  ] Started CUPS Scheduler.
[  OK  ] Started ACPI Events Check.
[  OK  ] Reached target Paths.
[  OK  ] Started Daily Cleanup of Temporary Directories.
[  OK  ] Listening on CUPS Scheduler.
[  OK  ] Started Message of the Day.
[  OK  ] Listening on UUID daemon activation socket.
[  OK  ] Started Daily apt download activities.
[  OK  ] Started Daily apt upgrade and clean activities.
[  OK  ] Listening on D-Bus System Message Bus Socket.
[  OK  ] Listening on ACPID Listen Socket.
[  OK  ] Started Trigger anacron every hour.
[  OK  ] Reached target Timers.
         Starting Socket activation for snappy daemon.
[  OK  ] Listening on Avahi mDNS/DNS-SD Stack Activation Socket.
         Starting Raise network interfaces...
[  OK  ] Listening on Socket activation for snappy daemon.
[  OK  ] Reached target Sockets.
[  OK  ] Reached target Basic System.
[  OK  ] Started ACPI event daemon.
         Starting Thermal Daemon Service...
         Starting Avahi mDNS/DNS-SD Stack...
         Starting System Logging Service...
         Starting LSB: automatic crash report generation...
         Starting Disk Manager...
         Starting Accounts Service...
[  OK  ] Reached target Login Prompts.
         Starting Dispatcher daemon for systemd-networkd...
         Starting Bluetooth service...
[  OK  ] Started Set the CPU Frequency Scaling governor.
[  OK  ] Started D-Bus System Message Bus.
         Starting Network Manager...
         Starting Snappy daemon...
         Starting Login Service...
         Starting Save/Restore Sound Card State...
[  OK  ] Started irqbalance daemon.
[  OK  ] Started CUPS Scheduler.
         Starting Detect the available GPUs and deal with any system changes...
         Starting Modem Manager...
[  OK  ] Started Regular background program processing daemon.
         Starting WPA supplicant...
[  OK  ] Started Run anacron jobs.
         Starting LSB: Speech Dispatcher...
         Starting LSB: Record successful boot for GRUB...
         Starting Restore /etc/resolv.conf if the system crashed before the ppp link was shut down...
[FAILED] Failed to start Avahi mDNS/DNS-SD Stack.
See 'systemctl status avahi-daemon.service' for details.
[  OK  ] Started LSB: automatic crash report generation.
[FAILED] Failed to start Bluetooth service.
See 'systemctl status bluetooth.service' for details.
[  OK  ] Started Restore /etc/resolv.conf if the system crashed before the ppp link was shut down.
[FAILED] Failed to start Disk Manager.
See 'systemctl status udisks2.service' for details.
[FAILED] Failed to start System Logging Service.
See 'systemctl status rsyslog.service' for details.
[FAILED] Failed to start Accounts Service.
See 'systemctl status accounts-daemon.service' for details.
[  OK  ] Started Save/Restore Sound Card State.
[FAILED] Failed to start Dispatcher daemon for systemd-networkd.
See 'systemctl status networkd-dispatcher.service' for details.
[  OK  ] Started D-Bus System Message Bus.
[  OK  ] Mounted Mount unit for gnome-calculator, revision 180.
[  OK  ] Mounted Mount unit for gnome-3-26-1604, revision 70.
[  OK  ] Started Show Plymouth Boot Screen.
[  OK  ] Started Forward Password Requests to Plymouth Directory Watch.
[  OK  ] Reached target Local Encrypted Volumes.
[  OK  ] Mounted Mount unit for gnome-logs, revision 37.
[  OK  ] Mounted Mount unit for gtk-common-themes, revision 319.
[  OK  ] Mounted Mount unit for gnome-system-monitor, revision 51.
[  OK  ] Mounted Mount unit for core, revision 4917.
[  OK  ] Mounted Mount unit for core18, revision 1288.
[  OK  ] Found device SAMSUNG_SSD_PM871b_M.2_2280_128GB EFI\x20System\x20Partition.
[  OK  ] Listening on Load/Save RF Kill Switch Status /dev/rfkill Watch.
         Starting File System Check on /dev/disk/by-uuid/F437-EF70...
         Starting Load/Save RF Kill Switch Status...
[  OK  ] Started File System Check Daemon to report status.
[  OK  ] Found device SAMSUNG_SSD_PM871b_M.2_2280_128GB 2.
         Mounting /mnt/sda...
[  OK  ] Mounted /mnt/sda.
[  OK  ] Started File System Check on /dev/disk/by-uuid/F437-EF70.
         Mounting /boot/efi...
[  OK  ] Mounted /boot/efi.
[  OK  ] Reached target Local File Systems.
         Starting Create Volatile Files and Directories...
         Starting Set console font and keymap...
         Starting Tell Plymouth To Write Out Runtime Data...
         Starting Clean up any mess left by 0dns-up...
         Starting AppArmor initialization...
[  OK  ] Started Set console font and keymap.
[FAILED] Failed to start Create Volatile Files and Directories.
See 'systemctl status systemd-tmpfiles-setup.service' for details.
[  OK  ] Started Clean up any mess left by 0dns-up.
[  OK  ] Started Tell Plymouth To Write Out Runtime Data.
         Starting Network Time Synchronization...
         Starting Network Name Resolution...
         Starting Update UTMP about System Boot/Shutdown...
[  OK  ] Started Load/Save RF Kill Switch Status.
         Starting Tell Plymouth To Write Out Runtime Data...
         Starting Create Volatile Files and Directories...
         Starting Create Static Device Nodes in /dev...
[  OK  ] Started Update UTMP about System Boot/Shutdown.
[FAILED] Failed to start Create Static Device Nodes in /dev.
See 'systemctl status systemd-tmpfiles-setup-dev.service' for details.
[  OK  ] Started Tell Plymouth To Write Out Runtime Data.
[FAILED] Failed to start Create Volatile Files and Directories.
See 'systemctl status systemd-tmpfiles-setup.service' for details.
[  OK  ] Created slice system-systemd\x2dbacklight.slice.
         Starting Load/Save Screen Backlight&#8230;ess of leds:dell::kbd_backlight...
[  OK  ] Started Load/Save Screen Backlight &#8230;tness of leds:dell::kbd_backlight.
[  OK  ] Started AppArmor initialization.
         Starting Raise network interfaces...
[  OK  ] Started Raise network interfaces.
[FAILED] Failed to start Network Time Synchronization.
See 'systemctl status systemd-timesyncd.service' for details.
[FAILED] Failed to start Network Name Resolution.
See 'systemctl status systemd-resolved.service' for details.
[  OK  ] Stopped Network Name Resolution.
         Starting Network Name Resolution...
[  OK  ] Stopped Network Time Synchronization.
         Starting Network Time Synchronization...
[FAILED] Failed to start Network Time Synchronization.
See 'systemctl status systemd-timesyncd.service' for details.
[  OK  ] Stopped Network Time Synchronization.
         Starting Network Time Synchronization...
[FAILED] Failed to start Network Name Resolution.
See 'systemctl status systemd-resolved.service' for details.
[  OK  ] Stopped Network Name Resolution.
         Starting Network Name Resolution...
         Starting Load/Save Screen Backlight Brightness of backlight:intel_backlight...
[  OK  ] Reached target Sound Card.
[  OK  ] Started Load/Save Screen Backlight Brightness of backlight:intel_backlight.
         Starting Create Static Device Nodes in /dev...
         Starting Tell Plymouth To Write Out Runtime Data...
         Starting Create Volatile Files and Directories...
[FAILED] Failed to start Create Static Device Nodes in /dev.
See 'systemctl status systemd-tmpfiles-setup-dev.service' for details.
[FAILED] Failed to start Create Volatile Files and Directories.
See 'systemctl status systemd-tmpfiles-setup.service' for details.
[FAILED] Failed to start Network Time Synchronization.
See 'systemctl status systemd-timesyncd.service' for details.
[  OK  ] Stopped Network Time Synchronization.
         Starting Network Time Synchronization...
[FAILED] Failed to start Network Name Resolution.
See 'systemctl status systemd-resolved.service' for details.
[  OK  ] Stopped Network Name Resolution.
         Starting Network Name Resolution...
[FAILED] Failed to start Network Time Synchronization.
See 'systemctl status systemd-timesyncd.service' for details.
[  OK  ] Stopped Network Time Synchronization.
         Starting Network Time Synchronization...
[FAILED] Failed to start Network Name Resolution.
See 'systemctl status systemd-resolved.service' for details.
[  OK  ] Stopped Network Name Resolution.
         Starting Network Name Resolution...
[FAILED] Failed to start Network Name Resolution.
See 'systemctl status systemd-resolved.service' for details.
[FAILED] Failed to start Network Time Synchronization.
See 'systemctl status systemd-timesyncd.service' for details.
[  OK  ] Stopped Network Time Synchronization.
[FAILED] Failed to start Network Time Synchronization.
See 'systemctl status systemd-timesyncd.service' for details.
[  OK  ] Stopped Network Name Resolution.
[FAILED] Failed to start Network Name Resolution.
See 'systemctl status systemd-resolved.service' for details.
[  OK  ] Reached target System Time Synchronized.
[  OK  ] Reached target Host and Network Name Lookups.
[  OK  ] Started Tell Plymouth To Write Out Runtime Data.
[  OK  ] Reached target System Initialization.
[  OK  ] Started Trigger anacron every hour.
         Starting Socket activation for snappy daemon.
[  OK  ] Started CUPS Scheduler.
[  OK  ] Started Message of the Day.
[  OK  ] Listening on D-Bus System Message Bus Socket.
[  OK  ] Started Daily Cleanup of Temporary Directories.
[  OK  ] Started Discard unused blocks once a week.
[  OK  ] Started Daily apt download activities.
[  OK  ] Listening on Avahi mDNS/DNS-SD Stack Activation Socket.
[  OK  ] Started Daily apt upgrade and clean activities.
[  OK  ] Reached target Timers.
[  OK  ] Listening on CUPS Scheduler.
[  OK  ] Started ACPI Events Check.
[  OK  ] Reached target Paths.
[  OK  ] Listening on ACPID Listen Socket.
[  OK  ] Listening on UUID daemon activation socket.
[  OK  ] Listening on Socket activation for snappy daemon.
[  OK  ] Reached target Sockets.
[  OK  ] Reached target Basic System.
         Starting Modem Manager...
[  OK  ] Started Regular background program processing daemon.
         Starting LSB: automatic crash report generation...
         Starting Login Service...
         Starting Avahi mDNS/DNS-SD Stack...
[  OK  ] Reached target Login Prompts.
         Starting Disk Manager...
         Starting NVIDIA Persistence Daemon...
[  OK  ] Started ACPI event daemon.
[  OK  ] Started irqbalance daemon.
[  OK  ] Started CUPS Scheduler.
         Starting Thermal Daemon Service...
         Starting LSB: Record successful boot for GRUB...
[  OK  ] Started Run anacron jobs.
         Starting Dispatcher daemon for systemd-networkd...
         Starting Accounts Service...
[  OK  ] Started Set the CPU Frequency Scaling governor.
         Starting System Logging Service...
         Starting Save/Restore Sound Card State...
         Starting Bluetooth service...
[  OK  ] Started D-Bus System Message Bus.
         Starting Network Manager...
         Starting WPA supplicant...
         Starting Restore /etc/resolv.conf if the system crashed before the ppp link was shut down...
         Starting LSB: Speech Dispatcher...
         Starting Detect the available GPUs and deal with any system changes...
         Starting Snappy daemon...
[FAILED] Failed to start Modem Manager.
See 'systemctl status ModemManager.service' for details.
[  OK  ] Started LSB: automatic crash report generation.
[FAILED] Failed to start Avahi mDNS/DNS-SD Stack.
See 'systemctl status avahi-daemon.service' for details.
[  OK  ] Started LSB: Record successful boot for GRUB.
[FAILED] Failed to start Bluetooth service.
See 'systemctl status bluetooth.service' for details.
[  OK  ] Started Restore /etc/resolv.conf if the system crashed before the ppp link was shut down.
[FAILED] Failed to start NVIDIA Persistence Daemon.
See 'systemctl status nvidia-persistenced.service' for details.
[FAILED] Failed to start Dispatcher daemon for systemd-networkd.
See 'systemctl status networkd-dispatcher.service' for details.
[FAILED] Failed to start Accounts Service.
See 'systemctl status accounts-daemon.service' for details.
[FAILED] Failed to start System Logging Service.
See 'systemctl status rsyslog.service' for details.
[FAILED] Failed to start Disk Manager.
See 'systemctl status udisks2.service' for details.
[  OK  ] Started Save/Restore Sound Card State.
[  OK  ] Started D-Bus System Message Bus.
[  OK  ] Reached target Bluetooth.
[  OK  ] Started Make remote CUPS printers available locally.
[  OK  ] Started Snappy daemon.
[FAILED] Failed to start Login Service.
See 'systemctl status systemd-logind.service' for details.
[FAILED] Failed to start Thermal Daemon Service.
See 'systemctl status thermald.service' for details.
[  OK  ] Started LSB: Speech Dispatcher.
[  OK  ] Started Detect the available GPUs and deal with any system changes.
[FAILED] Failed to start WPA supplicant.
See 'systemctl status wpa_supplicant.service' for details.
[  OK  ] Started D-Bus System Message Bus.
[  OK  ] Stopped Login Service.
         Starting Login Service...
[  OK  ] Stopped System Logging Service.
         Starting System Logging Service...
         Starting Wait until snapd is fully seeded...
[  OK  ] Started D-Bus System Message Bus.
[  OK  ] Mounted Mount unit for core, revision 4917.
[  OK  ] Mounted Mount unit for core18, revision 1288.
[  OK  ] Started Show Plymouth Boot Screen.
[  OK  ] Reached target Local Encrypted Volumes.
[  OK  ] Started Forward Password Requests to Plymouth Directory Watch.
[  OK  ] Mounted Mount unit for gnome-characters, revision 103.
[  OK  ] Mounted Mount unit for chromium, revision 971.
[  OK  ] Mounted Mount unit for gnome-logs, revision 37.
[  OK  ] Mounted Mount unit for gnome-3-26-1604, revision 70.
[  OK  ] Mounted Mount unit for spotify, revision 36.
[  OK  ] Listening on Load/Save RF Kill Switch Status /dev/rfkill Watch.
         Starting Load/Save RF Kill Switch Status...
         Starting Create Static Device Nodes in /dev...
[FAILED] Failed to start Create Static Device Nodes in /dev.
See 'systemctl status systemd-tmpfiles-setup-dev.service' for details.
[  OK  ] Started Load/Save RF Kill Switch Status.
[  OK  ] Found device SAMSUNG_SSD_PM871b_M.2_2280_128GB EFI\x20System\x20Partition.
         Starting File System Check on /dev/disk/by-uuid/F437-EF70...
[  OK  ] Started File System Check Daemon to report status.
[  OK  ] Started File System Check on /dev/disk/by-uuid/F437-EF70.
         Mounting /boot/efi...
[  OK  ] Mounted /boot/efi.
[  OK  ] Reached target Local File Systems.
         Starting Tell Plymouth To Write Out Runtime Data...
         Starting Create Volatile Files and Directories...
         Starting AppArmor initialization...
         Starting Clean up any mess left by 0dns-up...
         Starting Set console font and keymap...
[  OK  ] Started Set console font and keymap.
[FAILED] Failed to start Create Volatile Files and Directories.
See 'systemctl status systemd-tmpfiles-setup.service' for details.
[  OK  ] Started Clean up any mess left by 0dns-up.
         Starting Network Name Resolution...
         Starting Network Time Synchronization...
         Starting Update UTMP about System Boot/Shutdown...
[  OK  ] Started Tell Plymouth To Write Out Runtime Data.
[  OK  ] Created slice system-systemd\x2dbacklight.slice.
         Starting Load/Save Screen Backlight Brightness of leds:dell::kbd_backlight...
[  OK  ] Started Update UTMP about System Boot/Shutdown.
[  OK  ] Started Load/Save Screen Backlight Brightness of leds:dell::kbd_backlight.
[  OK  ] Started AppArmor initialization.
         Starting Raise network interfaces...
[  OK  ] Started Raise network interfaces.
[FAILED] Failed to start Network Name Resolution.
See 'systemctl status systemd-resolved.service' for details.
[FAILED] Failed to start Network Time Synchronization.
See 'systemctl status systemd-timesyncd.service' for details.
[  OK  ] Stopped Network Time Synchronization.
         Starting Network Time Synchronization...
[  OK  ] Stopped Network Name Resolution.
         Starting Network Name Resolution...
         Starting Create Static Device Nodes in /dev...
         Starting Create Volatile Files and Directories...
         Starting Tell Plymouth To Write Out Runtime Data...
[FAILED] Failed to start Create Static Device Nodes in /dev.
See 'systemctl status systemd-tmpfiles-setup-dev.service' for details.
[  OK  ] Started Tell Plymouth To Write Out Runtime Data.
[FAILED] Failed to start Create Volatile Files and Directories.
See 'systemctl status systemd-tmpfiles-setup.service' for details.
[FAILED] Failed to start Network Name Resolution.
See 'systemctl status systemd-resolved.service' for details.
[  OK  ] Stopped Network Name Resolution.
         Starting Network Name Resolution...
[FAILED] Failed to start Network Time Synchronization.
See 'systemctl status systemd-timesyncd.service' for details.
[  OK  ] Stopped Network Time Synchronization.
         Starting Network Time Synchronization...
[FAILED] Failed to start Network Name Resolution.
See 'systemctl status systemd-resolved.service' for details.
[  OK  ] Stopped Network Name Resolution.
         Starting Network Name Resolution...
[FAILED] Failed to start Network Time Synchronization.
See 'systemctl status systemd-timesyncd.service' for details.
[  OK  ] Stopped Network Time Synchronization.
         Starting Network Time Synchronization...
         Starting Load/Save Screen Backlight Brightness of backlight:intel_backlight...
[  OK  ] Reached target Sound Card.
[FAILED] Failed to start Network Name Resolution.
See 'systemctl status systemd-resolved.service' for details.
[FAILED] Failed to start Network Time Synchronization.
See 'systemctl status systemd-timesyncd.service' for details.
[  OK  ] Stopped Network Time Synchronization.
         Starting Network Time Synchronization...
[  OK  ] Stopped Network Name Resolution.
         Starting Network Name Resolution...
[  OK  ] Started Load/Save Screen Backlight Brightness of backlight:intel_backlight.
[FAILED] Failed to start Network Name Resolution.
See 'systemctl status systemd-resolved.service' for details.
[  OK  ] Stopped Network Name Resolution.
[FAILED] Failed to start Network Name Resolution.
See 'systemctl status systemd-resolved.service' for details.
[  OK  ] Reached target Host and Network Name Lookups.
[FAILED] Failed to start Network Time Synchronization.
See 'systemctl status systemd-timesyncd.service' for details.
[  OK  ] Stopped Network Time Synchronization.
[FAILED] Failed to start Network Time Synchronization.
See 'systemctl status systemd-timesyncd.service' for details.
[  OK  ] Reached target System Time Synchronized.
[  OK  ] Reached target System Initialization.
         Starting Socket activation for snappy daemon.
[  OK  ] Started Daily Cleanup of Temporary Directories.
[  OK  ] Listening on D-Bus System Message Bus Socket.
[  OK  ] Started Trigger anacron every hour.
[  OK  ] Started Message of the Day.
[  OK  ] Listening on UUID daemon activation socket.
[  OK  ] Started Discard unused blocks once a week.
[  OK  ] Listening on ACPID Listen Socket.
[  OK  ] Started Daily apt download activities.
[  OK  ] Started Daily apt upgrade and clean activities.
[  OK  ] Reached target Timers.
[  OK  ] Started CUPS Scheduler.
[  OK  ] Started ACPI Events Check.
[  OK  ] Reached target Paths.
[  OK  ] Listening on CUPS Scheduler.
[  OK  ] Listening on Avahi mDNS/DNS-SD Stack Activation Socket.
[  OK  ] Listening on Socket activation for snappy daemon.
[  OK  ] Reached target Sockets.
[  OK  ] Reached target Basic System.
[  OK  ] Started CUPS Scheduler.
         Starting Login Service...
         Starting NVIDIA Persistence Daemon...
[  OK  ] Started irqbalance daemon.
         Starting Dispatcher daemon for systemd-networkd...
[  OK  ] Started ACPI event daemon.
         Starting LSB: automatic crash report generation...
         Starting Detect the available GPUs and deal with any system changes...
         Starting System Logging Service...
[  OK  ] Started Run anacron jobs.
         Starting Avahi mDNS/DNS-SD Stack...
[  OK  ] Started D-Bus System Message Bus.
[  OK  ] Mounted Mount unit for chromium, revision 971.
[  OK  ] Started Show Plymouth Boot Screen.
[  OK  ] Reached target Local Encrypted Volumes.
[  OK  ] Started Forward Password Requests to Plymouth Directory Watch.
[  OK  ] Mounted Mount unit for gnome-characters, revision 103.
[  OK  ] Mounted Mount unit for gnome-3-26-1604, revision 70.
[  OK  ] Mounted Mount unit for gtk-common-themes, revision 319.
[  OK  ] Mounted Mount unit for gnome-calculator, revision 180.
[  OK  ] Mounted Mount unit for gnome-logs, revision 37.
[  OK  ] Listening on Load/Save RF Kill Switch Status /dev/rfkill Watch.
         Starting Load/Save RF Kill Switch Status...
[  OK  ] Found device SAMSUNG_SSD_PM871b_M.2_2280_128GB EFI\x20System\x20Partition.
         Starting File System Check on /dev/disk/by-uuid/F437-EF70...
[  OK  ] Started File System Check Daemon to report status.
[  OK  ] Started Load/Save RF Kill Switch Status.
         Starting Create Static Device Nodes in /dev...
[  OK  ] Started File System Check on /dev/disk/by-uuid/F437-EF70.
         Mounting /boot/efi...
[FAILED] Failed to start Create Static Device Nodes in /dev.
See 'systemctl status systemd-tmpfiles-setup-dev.service' for details.
[  OK  ] Mounted /boot/efi.
[  OK  ] Reached target Local File Systems.
         Starting Tell Plymouth To Write Out Runtime Data...
         Starting Create Volatile Files and Directories...
         Starting AppArmor initialization...
         Starting Clean up any mess left by 0dns-up...
         Starting Set console font and keymap...
[  OK  ] Started Set console font and keymap.
[FAILED] Failed to start Create Volatile Files and Directories.
See 'systemctl status systemd-tmpfiles-setup.service' for details.
         Starting Update UTMP about System Boot/Shutdown...
         Starting Network Time Synchronization...
         Starting Network Name Resolution...
[  OK  ] Started Tell Plymouth To Write Out Runtime Data.
[  OK  ] Started Clean up any mess left by 0dns-up.
[  OK  ] Started Update UTMP about System Boot/Shutdown.
[  OK  ] Created slice system-systemd\x2dbacklight.slice.
         Starting Load/Save Screen Backlight Brightness of leds:dell::kbd_backlight...
[  OK  ] Started Load/Save Screen Backlight Brightness of leds:dell::kbd_backlight.
[  OK  ] Started AppArmor initialization.
         Starting Raise network interfaces...
[  OK  ] Started Raise network interfaces.
[FAILED] Failed to start Network Name Resolution.
See 'systemctl status systemd-resolved.service' for details.
[  OK  ] Stopped Network Name Resolution.
         Starting Network Name Resolution...
[FAILED] Failed to start Network Time Synchronization.
See 'systemctl status systemd-timesyncd.service' for details.
[  OK  ] Stopped Network Time Synchronization.
         Starting Network Time Synchronization...
[FAILED] Failed to start Network Name Resolution.
See 'systemctl status systemd-resolved.service' for details.
[FAILED] Failed to start Network Time Synchronization.
See 'systemctl status systemd-timesyncd.service' for details.
         Starting Tell Plymouth To Write Out Runtime Data...
         Starting Create Static Device Nodes in /dev...
[  OK  ] Stopped Network Time Synchronization.
[  OK  ] Stopped Network Name Resolution.
         Starting Create Volatile Files and Directories...
[  OK  ] Reached target Sound Card.
         Starting Load/Save Screen Backlight Brightness of backlight:intel_backlight...
[FAILED] Failed to start Create Static Device Nodes in /dev.
See 'systemctl status systemd-tmpfiles-setup-dev.service' for details.
[FAILED] Failed to start Create Volatile Files and Directories.
See 'systemctl status systemd-tmpfiles-setup.service' for details.
         Starting Network Time Synchronization...
         Starting Network Name Resolution...
[  OK  ] Started Load/Save Screen Backlight Brightness of backlight:intel_backlight.
[FAILED] Failed to start Network Name Resolution.
See 'systemctl status systemd-resolved.service' for details.
[  OK  ] Stopped Network Name Resolution.
         Starting Network Name Resolution...
[  OK  ] Started Tell Plymouth To Write Out Runtime Data.
[FAILED] Failed to start Network Time Synchronization.
See 'systemctl status systemd-timesyncd.service' for details.
[  OK  ] Stopped Network Time Synchronization.
         Starting Network Time Synchronization...
[FAILED] Failed to start Network Name Resolution.
See 'systemctl status systemd-resolved.service' for details.
[  OK  ] Stopped Network Name Resolution.
         Starting Network Name Resolution...
[FAILED] Failed to start Network Time Synchronization.
See 'systemctl status systemd-timesyncd.service' for details.
[  OK  ] Stopped Network Time Synchronization.
         Starting Network Time Synchronization...
[FAILED] Failed to start Network Name Resolution.
See 'systemctl status systemd-resolved.service' for details.
[  OK  ] Stopped Network Name Resolution.
[FAILED] Failed to start Network Name Resolution.
See 'systemctl status systemd-resolved.service' for details.
[  OK  ] Reached target Host and Network Name Lookups.
[FAILED] Failed to start Network Time Synchronization.
See 'systemctl status systemd-timesyncd.service' for details.
[  OK  ] Stopped Network Time Synchronization.
[FAILED] Failed to start Network Time Synchronization.
See 'systemctl status systemd-timesyncd.service' for details.
[  OK  ] Reached target System Initialization.
[  OK  ] Listening on D-Bus System Message Bus Socket.
[  OK  ] Started ACPI Events Check.
[  OK  ] Started Daily Cleanup of Temporary Directories.
[  OK  ] Listening on CUPS Scheduler.
[  OK  ] Listening on UUID daemon activation socket.
[  OK  ] Listening on ACPID Listen Socket.
         Starting Socket activation for snappy daemon.
[  OK  ] Started CUPS Scheduler.
[  OK  ] Reached target Paths.
[  OK  ] Listening on Avahi mDNS/DNS-SD Stack Activation Socket.
[  OK  ] Reached target System Time Synchronized.
[  OK  ] Started Trigger anacron every hour.
[  OK  ] Started Message of the Day.
[  OK  ] Started Discard unused blocks once a week.
[  OK  ] Started Daily apt download activities.
[  OK  ] Started Daily apt upgrade and clean activities.
[  OK  ] Reached target Timers.
[  OK  ] Listening on Socket activation for snappy daemon.
[  OK  ] Reached target Sockets.
[  OK  ] Reached target Basic System.
[  OK  ] Started CUPS Scheduler.
[  OK  ] Reached target Login Prompts.
         Starting Thermal Daemon Service...
[  OK  ] Started irqbalance daemon.
         Starting Dispatcher daemon for systemd-networkd...
         Starting Login Service...
[  OK  ] Started Regular background program processing daemon.
         Starting Detect the available GPUs and deal with any system changes...
         Starting Accounts Service...
         Starting LSB: Speech Dispatcher...
         Starting Restore /etc/resolv.conf if the system crashed before the ppp link was shut down...
         Starting Disk Manager...
[  OK  ] Started Run anacron jobs.
         Starting LSB: Record successful boot for GRUB...
[  OK  ] Started ACPI event daemon.
[  OK  ] Started Set the CPU Frequency Scaling governor.
         Starting System Logging Service...
         Starting Save/Restore Sound Card State...
[  OK  ] Started D-Bus System Message Bus.
         Starting Network Manager...
         Starting LSB: automatic crash report generation...
         Starting Modem Manager...
         Starting WPA supplicant...
         Starting NVIDIA Persistence Daemon...
         Starting Avahi mDNS/DNS-SD Stack...
         Starting Bluetooth service...
         Starting Snappy daemon...
[  OK  ] Started Detect the available GPUs and deal with any system changes.
[  OK  ] Started Restore /etc/resolv.conf if the system crashed before the ppp link was shut down.
[FAILED] Failed to start Avahi mDNS/DNS-SD Stack.
See 'systemctl status avahi-daemon.service' for details.
[FAILED] Failed to start Dispatcher daemon for systemd-networkd.
See 'systemctl status networkd-dispatcher.service' for details.
[FAILED] Failed to start Disk Manager.
See 'systemctl status udisks2.service' for details.
[FAILED] Failed to start System Logging Service.
See 'systemctl status rsyslog.service' for details.
[FAILED] Failed to start NVIDIA Persistence Daemon.
See 'systemctl status nvidia-persistenced.service' for details.
[FAILED] Failed to start Accounts Service.
See 'systemctl status accounts-daemon.service' for details.
[  OK  ] Started Save/Restore Sound Card State.
[  OK  ] Started LSB: Speech Dispatcher.
[  OK  ] Started D-Bus System Message Bus.


```

How do you attach files to avoid these long entries? :D

Thank you!

---

### Post by deadflowr on 2020-01-05
> Restarting lightdm does not work. I realised that I don't have a lightm.conf file at this point, so I created one with minimal Information:
```
Greeter-session =lightdm-slick-greeter
User-session = Ubuntu
```
I hope that is correct.

Is that the whole output?
Where's the [Seat:*] ?

Also [s]the user-session[/s] it should be all lower case, as far as I'm aware.

But you seem to have a lot of issues beyond the login screen issue.

> How do you attach files to avoid these long entries? 
For general output use code tags, and if really really long output, you can use [pastebins]("https://wiki.ubuntu.com/Pastebin") such as [ubuntu pastebin]("https://paste.ubuntu.com/")
Then just add a link to it.
Links are easier to deal with than attached files.
No one wants to download a file for someone else's problems.
(I know I don't)

---

### Post by marius22 on 2020-01-06
Hello!

> **deadflowr said:**
> Is that the whole output?
Where's the [Seat:*] ?

Also [s]the user-session[/s] it should be all lower case, as far as I'm aware.

So I checked the LIghtDM and installed slick-greeter (Yep, I did not have it before...) . It created a new config file that contains all the basic stuff, also [Seat:*] now. 
Unfortunately the problem remains when installing Nvidia driver. 


> **deadflowr said:**
> 
But you seem to have a lot of issues beyond the login screen issue.

Yep, but this is the most annoying for now.

> **deadflowr said:**
> 
For general output use code tags, and if really really long output, you can use [pastebins]("https://wiki.ubuntu.com/Pastebin") such as [ubuntu pastebin]("https://paste.ubuntu.com/")
Then just add a link to it.
Links are easier to deal with than attached files.
No one wants to download a file for someone else's problems.
(I know I don't)
Thanks :)

---

