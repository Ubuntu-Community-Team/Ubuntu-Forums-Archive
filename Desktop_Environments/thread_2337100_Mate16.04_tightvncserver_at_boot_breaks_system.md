---
title: "Mate16.04 tightvncserver at boot breaks system"
date: 2016-09-14
forum: Desktop Environments
---

### Post by noabody2 on 2016-09-14
This will mess with your head!  I have discovered a completely reproducible problem with UbuntuMate16.04 where it is not possible to run tightvncserver at boot without breaking the operating system.  Specifically, Wi-Fi authentication, VPN, and USB (gvfs-mount) all fail.

I've successfully setup the server using both systemctl and rc.d. [https://www.raspberrypi.org/documentation/remote-access/vnc/](https://www.raspberrypi.org/documentation/remote-access/vnc/)  and [https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-16-04). Both methods result in the same failure.

Once the vncserver is running at boot, it's no longer possible to connect to a new (secured) Wi-Fi network as there is no password prompt.  Plugging a USB stick may work once but most often fails with message "unable to mount volume, an operation is already pending".

The moment the vnc server is stopped, it's like a gate is opened.  The pending USB mount and Wi-Fi connection both complete.  Here are my latest logs which is an output of "journalctl -e -n 50".  My best guess is that the VNC server is tying up PAM and the gnome-keyring.  

Perhaps it is assigned like a login session that can't properly complete because the VNC server attaches to a user profile that has not been logged in and is acting like a root process?  Seems like a security issue but I don't know enough about Linux to understand why it's happening.  I only know that I'm doing something that should work, based on the tutorials I'm using, but it causes an unexpected failure.

```

Sep 14 09:14:41 computer kernel: usb 1-2: USB disconnect, device number 7
Sep 14 09:14:45 computer kernel: usb 1-2: new high-speed USB device number 8 using ehci-pci
Sep 14 09:14:45 computer kernel: usb 1-2: New USB device found, idVendor=0781, idProduct=5581
Sep 14 09:14:45 computer kernel: usb 1-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Sep 14 09:14:45 computer kernel: usb 1-2: Product: SanDisk Ultra
Sep 14 09:14:45 computer kernel: usb 1-2: Manufacturer: SanDisk
Sep 14 09:14:45 computer kernel: usb 1-2: SerialNumber: 
Sep 14 09:14:45 computer kernel: usb-storage 1-2:1.0: USB Mass Storage device detected
Sep 14 09:14:45 computer kernel: scsi host5: usb-storage 1-2:1.0
Sep 14 09:14:45 computer mtp-probe[2406]: checking bus 1, device 8: "/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-2"
Sep 14 09:14:45 computer mtp-probe[2406]: bus: 1, device: 8 was not an MTP device
Sep 14 09:14:46 computer kernel: scsi 5:0:0:0: Direct-Access     SanDisk  SanDisk Ultra    PMAP PQ: 0 ANSI: 6
Sep 14 09:14:46 computer kernel: sd 5:0:0:0: Attached scsi generic sg2 type 0
Sep 14 09:14:46 computer kernel: sd 5:0:0:0: [sdc] 61767680 512-byte logical blocks: (31.6 GB/29.5 GiB)
Sep 14 09:14:46 computer kernel: sd 5:0:0:0: [sdc] Write Protect is off
Sep 14 09:14:46 computer kernel: sd 5:0:0:0: [sdc] Mode Sense: 2b 00 00 08
Sep 14 09:14:46 computer kernel: sd 5:0:0:0: [sdc] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Sep 14 09:14:47 computer kernel:  sdc: sdc1
Sep 14 09:14:47 computer kernel: sd 5:0:0:0: [sdc] Attached SCSI removable disk
Sep 14 09:15:04 computer NetworkManager[767]: <error> [1473866104.3447] vpn-connection[,0]: Failed to request VPN secrets #3: No agents were available for this request.
Sep 14 09:15:12 computer sudo[2457]:      user : TTY=pts/0 ; PWD=/home/user ; USER=root ; COMMAND=/bin/systemctl stop vncserver@1
Sep 14 09:15:12 computer sudo[2457]: pam_unix(sudo:session): session opened for user root by user(uid=0)
Sep 14 09:15:12 computer systemd[1]: Stopping Start TightVNC server at startup...
Sep 14 09:15:12 computer systemd[2460]: pam_unix(login:session): session opened for user user by (uid=0)
Sep 14 09:15:12 computer systemd[1]: Started Session 3 of user user.
Sep 14 09:15:13 computer vncserver[2460]: Killing Xtightvnc process ID 1062
Sep 14 09:15:13 computer org.a11y.atspi.Registry[1303]: XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":1"
Sep 14 09:15:13 computer org.a11y.atspi.Registry[1303]:       after 11 requests (11 known processed) with 0 events remaining.
Sep 14 09:15:13 computer systemd[2465]: pam_unix(login:session): session closed for user user
Sep 14 09:15:13 computer dbus[674]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.98" (uid=1000 pid=2465 comm="(sd-pam)          ") interface="org.freedesktop.login1.Manager" member="ReleaseSession" error name="(unset)" requested_reply="0" destination="org.freedesktop.login1" (uid=0 pid=727 comm="/lib/systemd/systemd-logind ")
Sep 14 09:15:13 computer systemd[2465]: pam_systemd(login:session): Failed to release session: Access denied
Sep 14 09:15:13 computer gcr-prompter[2367]: Gcr: caller vanished for callback /org/gnome/keyring/Prompt/p2@:1.5
Sep 14 09:15:13 computer gcr-prompter[2367]: Gcr: stopping prompting for operation /org/gnome/keyring/Prompt/p2@:1.5
Sep 14 09:15:13 computer gcr-prompter[2367]: Gcr: cancelling active prompting operation for /org/gnome/keyring/Prompt/p2@:1.5
Sep 14 09:15:13 computer gcr-prompter[2367]: Gcr: closing the prompt
Sep 14 09:15:13 computer gcr-prompter[2367]: Gcr: stopping prompting for operation /org/gnome/keyring/Prompt/p2@:1.5
Sep 14 09:15:13 computer gcr-prompter[2367]: Gcr: couldn't find the callback for prompting operation /org/gnome/keyring/Prompt/p2@:1.5
Sep 14 09:15:13 computer org.gtk.vfs.Daemon[1263]: A connection to the bus can't be made
Sep 14 09:15:13 computer org.gtk.vfs.Daemon[1263]: A connection to the bus can't be made
Sep 14 09:15:13 computer gcr-prompter[2367]: Gcr: completed password prompt for callback :1.5@/org/gnome/keyring/Prompt/p2
Sep 14 09:15:13 computer gcr-prompter[2367]: Gcr: sending the secret exchange: [sx-aes-1]\npublic=\n
Sep 14 09:15:13 computer gcr-prompter[2367]: Gcr: calling the PromptReady method on /org/gnome/keyring/Prompt/p2@:1.5
Sep 14 09:15:13 computer gcr-prompter[2367]: Gcr: stopping prompting for operation /org/gnome/keyring/Prompt/p2@:1.5
Sep 14 09:15:13 computer gcr-prompter[2367]: Gcr: couldn't find the callback for prompting operation /org/gnome/keyring/Prompt/p2@:1.5
Sep 14 09:15:13 computer gcr-prompter[2367]: Gcr: returned from the PromptReady method on /org/gnome/keyring/Prompt/p2@:1.5
Sep 14 09:15:13 computer gcr-prompter[2367]: lost name: org.gnome.keyring.SystemPrompter
Sep 14 09:15:13 computer gcr-prompter[2367]: couldn't connect to session bus
Sep 14 09:15:13 computer org.gnome.keyring.SystemPrompter[1263]: ** (gcr-prompter:2367): WARNING **: couldn't connect to session bus
Sep 14 09:15:13 computer org.gnome.keyring.SystemPrompter[1263]: ** (gcr-prompter:2367): WARNING **: couldn't connect to session bus
Sep 14 09:15:13 computer gcr-prompter[2367]: lost name: org.gnome.keyring.PrivatePrompter
Sep 14 09:15:13 computer gcr-prompter[2367]: couldn't connect to session bus
Sep 14 09:15:13 computer polkit-agent-helper-1[2433]: pam_unix(polkit-1:auth): conversation failed
Sep 14 09:15:13 computer polkit-agent-helper-1[2433]: pam_unix(polkit-1:auth): auth could not identify password for [user]
Sep 14 09:15:13 computer systemd[1]: Stopped Start TightVNC server at startup.
Sep 14 09:15:13 computer sudo[2457]: pam_unix(sudo:session): session closed for user root
Sep 14 09:15:13 computer polkitd(authority=local)[822]: Unregistered Authentication Agent for unix-session:2 (system bus name :1.69, object path /org/mate/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8) (disconnected from bus)
Sep 14 09:15:13 computer polkitd(authority=local)[822]: Operator of unix-session:2 FAILED to authenticate to gain authorization for action org.freedesktop.udisks2.filesystem-mount for system-bus-name::1.43 [<unknown>] (owned by unix-user:user)
Sep 14 09:15:13 computer kernel: FAT-fs (sdc1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.
Sep 14 09:15:13 computer udisksd[1449]: Mounted /dev/sdc1 at /media/user/MULTIBOOT on behalf of uid 1000

```

---

