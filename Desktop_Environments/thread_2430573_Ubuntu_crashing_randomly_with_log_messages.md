---
title: "Ubuntu crashing randomly with log messages"
date: 2019-11-04
forum: Desktop Environments
---

### Post by banyous on 2019-11-04
Hi,
I have ubuntu 18.04.3 LTS Installed on a lenovo laptop with intel graphic card, recently  the pc is rebooting randomly after about half hour or more of use,
Below the syslog messages I am getting after the crash:
Any Idea how to proceed? 
Thanks

 ```
[ OK ] Reached target Host and Network Name Lookups. 

  [ OK ] Started Restore /etc/resolv.conf if the system crashed before the opp link was shut down.
  [OK ] Started Save/Restore Sound Card State.
  [ OK ] Started LSB: Speech Dispatcher. 
  [ OK ] Started System Logging Service. 
  [ OK ] Started Avahi MDNS/DNS-SD Stack.
  [ OK ] Started Bluetooth service.
  [ OK ] Started Thermal Daemon Service.
  Starting Hostname Service...
  Starting Authorization Manager…
  [OK] Reached target Bluetooth. 
  [OK] Started Make remote CUPS printers available locally.
  [OK ] Started Hostname Service. 
  [OK] Started LSB: automatic crash report generation. 
  [ OK ] Started WPA supplicant.
  Started LSB: Record successful boot for GRUB.
  [OK ] Started Detect the available GPUs and deal with any system changes.
  Starting Manage, Install and Generate Color Profiles... 
  [OK ] Started LSB: Starts and stops Wicd. OK ] Started Authorization Manager.
  [OK ] Started Accounts Service.
  [ OK] 1 Started Modem Manager.
  [ OK ] Started Dispatcher daemon for systemd-networkd. 
  [ OK] Started Disk Manager.
  [ OK ] Started Manage, Install and Generate Color Profiles. 
  [ OK ] Started Network Manager.
  Starting Network Manager Wait Online... 
  OK 1 Reached target Network.
  [ OK ]Started Unattended Upgrades Shutdown.
  Starting OpenBSD Secure Shell server...
  Starting Permit User Sessions…
  [ OK ]Started Permit User Sessions.
  Starting Hold until boot process finishes up...
  Starting GNOME Display Manager.. 
  [ OK ]Started Hold until boot process finishes up.
  Starting Set console scheme... 
  [ OK ]Started Set console scheme. 
  [ OK ]Created slice system-getty.slice,
  Starting Network Manager Script Dispatcher Service... 
   UK 1 started GNOME Display Manager,
   UK 1 Started Network Manager script Dispatcher Service. 
  [ OK ]Created slice User Slice of gdm.
  Starting User Manager for UID 121,,, 1
  [ OK ]started session cl of user gom,
  [ OK ]started User Mariager for UID 121, [ 3896.458533) athiok oci 0000:01:00.0: failed to receive initialized event from target: 00000000 [ 3899.487303) athiok_bci 0000:01:00.0: failed to receive initialized event from target: 00000000
```

---

### Post by Autodave on 2019-11-04
Normally, rebooting on its own tells me that it is a memory problem: either defective or overheating.  Have you checked to make sure that fan is operating?  Are the air inlets and outlets free of dust and dirt?  Are you making sure that they are not being blocked or restricted while you operate it?  Once you are sure that sufficient air is going through, run a memory test on it.

---

