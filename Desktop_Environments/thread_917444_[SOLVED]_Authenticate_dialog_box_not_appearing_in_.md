---
title: "[SOLVED] Authenticate dialog box not appearing in Fluxbox"
date: 2008-09-11
forum: Desktop Environments
---

### Post by Patb on 2008-09-11
Hi. When I try to open network-admin, and click on the "Unlock" button, nothing happens. I do not get the "Authenticate" dialog box as I should so I cannot make any settings. I've done a fair quota of reading, searching and googling on this :).

I am running Fluxbox window manager on a full Gnome installation. In Fluxbox, the "gnome-keyring-daemon" is running in the background and I have tried turning it off, to no avail. 

If I log in on a default Gnome desktop, the problem does not happen - clicking on "Unlock" brings up the normal "Authenticate" dialog box. 

I do not understand this behaviour, nor where it might be coming from but I suspect it is fairly simple. Any guidance would be appreciated. Below is a threaded list of all running processes.

Cheers, Pat
```
pat@laptop:~$ ps -ejH
  PID  PGID   SID TTY          TIME CMD
    2     0     0 ?        00:00:00 kthreadd
    3     0     0 ?        00:00:00   migration/0
    4     0     0 ?        00:00:00   ksoftirqd/0
    5     0     0 ?        00:00:00   watchdog/0
    6     0     0 ?        00:00:00   migration/1
    7     0     0 ?        00:00:00   ksoftirqd/1
    8     0     0 ?        00:00:00   watchdog/1
    9     0     0 ?        00:00:00   events/0
   10     0     0 ?        00:00:00   events/1
   11     0     0 ?        00:00:00   khelper
   46     0     0 ?        00:00:00   kblockd/0
   47     0     0 ?        00:00:00   kblockd/1
   50     0     0 ?        00:00:00   kacpid
   51     0     0 ?        00:00:00   kacpi_notify
  133     0     0 ?        00:00:00   kseriod
  175     0     0 ?        00:00:00   pdflush
  176     0     0 ?        00:00:00   pdflush
  177     0     0 ?        00:00:00   kswapd0
  218     0     0 ?        00:00:00   aio/0
  219     0     0 ?        00:00:00   aio/1
 1411     0     0 ?        00:00:00   ksuspend_usbd
 1417     0     0 ?        00:00:00   khubd
 1597     0     0 ?        00:00:00   ata/0
 1601     0     0 ?        00:00:00   ata/1
 1603     0     0 ?        00:00:00   ata_aux
 1611     0     0 ?        00:00:00   scsi_eh_0
 1613     0     0 ?        00:00:00   scsi_eh_1
 2374     0     0 ?        00:00:00   scsi_eh_2
 2375     0     0 ?        00:00:00   usb-storage
 2966     0     0 ?        00:00:00   kpsmoused
 3031     0     0 ?        00:00:00   kmmcd
 3860     0     0 ?        00:00:00   mmcqd
 4848     0     0 ?        00:00:00   kondemand/0
 4849     0     0 ?        00:00:00   kondemand/1
    1     1     1 ?        00:00:01 init
 2680  2680  2680 ?        00:00:00   udevd
 4621  4621  4621 tty4     00:00:00   getty
 4622  4622  4622 tty5     00:00:00   getty
 4627  4627  4627 tty2     00:00:00   getty
 4628  4628  4628 tty3     00:00:00   getty
 4633  4633  4633 tty6     00:00:00   getty
 4814  4814  4814 ?        00:00:00   acpid
 4934  4934  4934 ?        00:00:00   syslogd
 4986  4985  4985 ?        00:00:00   dd
 4988  4988  4988 ?        00:00:00   klogd
 5010  5010  5010 ?        00:00:00   dbus-daemon
 5026  5026  5026 ?        00:00:00   NetworkManager
 5040  5040  5040 ?        00:00:00   NetworkManagerD
 5053  5053  5053 ?        00:00:00   system-tools-ba
 5073  5073  5073 ?        00:00:00   avahi-daemon
 5074  5074  5074 ?        00:00:00     avahi-daemon
 5116  5116  5116 ?        00:00:00   cupsd
 5169  5169  5169 ?        00:00:00   winbindd
 5184  5169  5169 ?        00:00:00     winbindd
 5208  5208  5208 ?        00:00:00   dhcdbd
 5559  5208  5208 ?        00:00:00     dhclient
 5227  5227  5227 ?        00:00:00   hald
 5231  5227  5227 ?        00:00:00     hald-runner
 5304  5227  5227 ?        00:00:00       hald-addon-inpu
 5310  5227  5227 ?        00:00:00       hald-addon-cpuf
 5311  5227  5227 ?        00:00:00       hald-addon-acpi
 5230  5230  5230 ?        00:00:00   console-kit-dae
 5381  5381  5381 ?        00:00:00   gdm
 5383  5383  5381 ?        00:00:00     gdm
 5394  5394  5394 tty7     00:00:07       Xorg
 5655  5655  5655 ?        00:00:00       fluxbox
 5734  5734  5734 ?        00:00:00         ssh-agent
 5743  5743  5743 ?        00:00:00         seahorse-agent
 5763  5655  5655 ?        00:00:00         conky
 5765  5655  5655 ?        00:00:00         evolution-alarm
 5801  5801  5801 ?        00:00:05         firefox
 5826  5826  5826 ?        00:00:00         xterm
 5827  5827  5827 pts/0    00:00:00           bash
 5892  5892  5827 pts/0    00:00:00             ps
 5423  5423  5423 ?        00:00:00   atd
 5440  5440  5440 ?        00:00:00   cron
 5541  5541  5541 tty1     00:00:00   getty
 5736  5655  5655 ?        00:00:00   gconfd-2
 5782  5782  5782 ?        00:00:00   bonobo-activati

```

---

### Post by dustigroove on 2008-09-11
Unfortunately no solution for you on my end... but sitting there with ya in the same boat.

This occurs under Openbox as well. So far I've not had much luck finding a solution to get PolicyKit and ConsoleKit to play nice when not under Gnome.

---

### Post by Patb on 2008-09-11
Thanks Dusti.  It is probably something fairly simple. I should have mentioned that I have a virtually identical setup on my desktop. On the desktop, the dialog box comes up as it should, whether I'm in a  Gnome or Fluxbox desktop. It is only on my laptop that it plays up.

Any suggestions would be welcome.  

Cheers, Pat

---

### Post by dustigroove on 2008-09-12
A couple of questions...

Q1) Are you using Gnome with Fluxbox as the WM or straight Fluxbox (Fluxbox as the session versus Gnome/Fluxbox at login)?

Q2) Did you upgrade up to Hardy or do a fresh install?

---

### Post by p_quarles on 2008-09-12
I would suggest you create a launcher in ~/.fluxbox/menu that runs the network manager in superuser mode, using gksu. This will get around the need to "authenticate."

Fluxbox doesn't handle any background processes, so at a certain point getting GNOME stuff to work in Fluxbox essentially means reconstructing GNOME with Fluxbox as the window manager. More work than it's worth, imo.

---

### Post by Patb on 2008-09-12
Thanks again Dusti. I am using Gnome with Fluxbox as the WM. I use GDM and can log in on a standard Gnome desktop, in which case this problem doesn't occur. And this is a very recent fresh install - with no "dead wood" to speak of. 

P_quarles, thank you too for the suggestion. I can of course launch network-admin from a terminal using gksu but in that case, the unlock button and everything else is greyed out. Launching it without administrative privileges from a terminal behaves identically as starting it from the menu. But I do get the following errors in the console:
```
pat@laptop:~$ network-admin
** (network-admin:8200): CRITICAL **: Cannot create session bus: Failed to connect to socket /tmp/dbus-OolW7iPVIw: Connection refused
(network-admin:8200): Gtk-WARNING **: Unknown property: GtkComboBox.items
```
I think this problem has something to do with polkit which for some reason is not able to invoke the authenticate process. If I have gnome system monitor running in the (literal) background as I click on the "Unlock" button, polkit does not appear on the processes list. If I am in Gnome WM, it does, and the "Authenticate" dialog comes up. 
> Getting GNOME stuff to work in Fluxbox essentially means reconstructing GNOME with Fluxbox as the window manager. More work than it's worth, imo
I tend to agree. That is why I simply add Fluxbox as an alternative WM on top of a standard Gnome installation. Almost everything does work in Fluxbox if you use the CLI commands. But I think that is unrelated to this problem - my desktop computer has an identical Fluxbox setup and this problem does not occur on it. 

Are there any suggestions on how to coax polkit to throw up the "Authenticate" dialog when I click the network-admin "Unlock" button?  

Cheers, Pat.

---

### Post by Patb on 2008-09-12
Found a solution - probably a bit rough but it seems to have worked. I renamed the folder ~/.dbus (from recovery mode in case the system recreated an exact copy) then rebooted. A "clean" ~/.dbus directory was then created automatically. The unruly "Authenticate" dialog now comes up as expected! 

I don't understand dbus or polkit so I'm not exactly sure why this worked but it seems one couldn't call the other in some way, presumably because the settings under that ~/.dbus directory were not correct. The hint came from the error message I quoted. 

Dusti, if this works for you, you might post.  I'll mark this solved.

Cheers, Pat

---

### Post by dustigroove on 2008-09-12
Still no joy for me, but glad you got yours fixed!

Mine is most likely due to the fact that I've taken the hard road and am not using Fluxbox as the WM for Gnome... I guess I'm just fond of re-creating the wheel sometimes! ;-)

(I'll post a new thread if I don't get it sorted out on my own, thanks!)

Cheers

---

### Post by Buce on 2009-03-17
dustigroove, if you found a workaround for this, could you post it? I've got the same problem. :/

---

