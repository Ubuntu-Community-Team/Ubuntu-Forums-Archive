---
title: "Flickering desktop! (intel 865G VGA chipset)"
date: 2006-06-25
forum: Desktop Environments
---

### Post by quedigg on 2006-06-25
Hello fellows!
Unbuntu team represented a really great desktop, lite-weight ,user-friendly and completely free miracle os!
however,it's working smoothly on my machine except a couple os issues :
[LIST][*]Flickering Desktop although the refresh rate is (85 Hz) and the system support the intell 865G VGA [*]On any activity ,especially scrolling web pages , i laways hear a busy sound from my harddisk (the swap partion is 512 Mb size ,also the RAM installed )


[/LIST]

Thanks All !

---

### Post by NESFreak on 2006-06-25
maybe 85hz is to high?
try 60hz or something like that

---

### Post by taurus on 2006-06-25
For flickering, make sure you have both vertical and horizontal refreshing rates right in /etc/X11/xorg.conf!  Otherwise, save the original copy of /etc/X11/xorg.conf and configure your X again as
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak <-- making a backup...
sudo dpkg-reconfigure xserver-xorg <-- configuring your X again...

```
How many apps/progs do you have open anyway?  What is the output of these two commands from a terminal (Applications -> Accessories -> Terminal)?
```

free
ps -A

```

---

### Post by quedigg on 2006-06-25
Thanks! 
here is the outpuy of those commands :>              total       used       free     shared    buffers     cached
Mem:        483812     303976     179836          0       6124     159964
-/+ buffers/cache:     137888     345924
Swap:       433712          0     433712
amr@amr-desktop:~$ ps -A
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 ksoftirqd/0
    3 ?        00:00:00 watchdog/0
    4 ?        00:00:00 events/0
    5 ?        00:00:00 khelper
    6 ?        00:00:00 kthread
    8 ?        00:00:00 kblockd/0
    9 ?        00:00:00 kacpid
  122 ?        00:00:00 pdflush
  123 ?        00:00:00 pdflush
  125 ?        00:00:00 aio/0
  124 ?        00:00:00 kswapd0
  712 ?        00:00:00 kseriod
 1805 ?        00:00:00 khubd
 1926 ?        00:00:00 kjournald
 2152 ?        00:00:00 udevd
 2938 ?        00:00:00 shpchpd_event
 3507 ?        00:00:00 dhclient3
 3814 ?        00:00:00 acpid
 4214 ?        00:00:00 gdm
 4226 ?        00:00:00 gdm
 4248 tty7     00:00:08 Xorg
 4257 ?        00:00:00 hpiod
 4281 ?        00:00:00 python
 4328 ?        00:00:00 cupsd
 4351 ?        00:00:00 dbus-daemon
 4366 ?        00:00:01 hald
 4367 ?        00:00:00 hald-runner
 4372 ?        00:00:00 hald-addon-acpi
 4432 ?        00:00:00 hald-addon-keyb
 4443 ?        00:00:00 hald-addon-stor
 4444 ?        00:00:00 hald-addon-stor
 4518 ?        00:00:00 hcid
 4522 ?        00:00:00 sdpd
 4535 ?        00:00:00 krfcommd
 4548 ?        00:00:00 mdadm
 4582 ?        00:00:00 atd
 4595 ?        00:00:00 cron
 4644 ?        00:00:00 apache2
 4645 ?        00:00:00 apache2
 4663 ?        00:00:00 apache2
 4664 ?        00:00:00 apache2
 4767 tty1     00:00:00 getty
 4768 tty2     00:00:00 getty
 4769 tty3     00:00:00 getty
 4770 tty4     00:00:00 getty
 4771 tty5     00:00:00 getty
 4772 tty6     00:00:00 getty
 4783 ?        00:00:00 x-session-manag
 4825 ?        00:00:00 ssh-agent
 4828 ?        00:00:00 dbus-launch
 4829 ?        00:00:00 dbus-daemon
 4831 ?        00:00:00 gconfd-2
 4834 ?        00:00:00 gnome-keyring-d
 4836 ?        00:00:00 bonobo-activati
 4838 ?        00:00:00 gnome-settings-
 4840 ?        00:00:00 esd
 4848 ?        00:00:00 metacity
 4853 ?        00:00:01 gnome-panel
 4855 ?        00:00:01 nautilus
 4860 ?        00:00:00 gnome-volume-ma
 4866 ?        00:00:00 update-notifier
 4871 ?        00:00:00 gnome-vfs-daemo
 4875 ?        00:00:00 gnome-cups-icon
 4879 ?        00:00:00 trashapplet
 4889 ?        00:00:00 gnome-power-man
 4895 ?        00:00:00 mapping-daemon
 4900 ?        00:00:00 mixer_applet2
 4902 ?        00:00:00 clock-applet
 4909 ?        00:00:11 firefox-bin
 4924 ?        00:00:00 gnome-screensav
 5016 ?        00:00:00 gnome-terminal
 5017 ?        00:00:00 gnome-pty-helpe
 5018 pts/0    00:00:00 bash
 5043 pts/0    00:00:00 ps

and i've switched to 60 Hz RR ,still flickering ,but reduced

---

### Post by quedigg on 2006-06-25
and i'm only using Firefox at the moment!

---

### Post by taurus on 2006-06-25
What is the output of "free" command then?

And for flickering, see if you have vertical and horizontal refeshing rates in /etc/X11/xorg.conf!  If you do, make sure they are the right values for your monitor.  Otherwise, configure your X again with
```

sudo dpkg-reconfigure xserver-xrog

```

---

### Post by quedigg on 2006-06-25
[IMG]http://img57.imageshack.us/img57/2224/screenshot8kh.jpg[/IMG]

---

### Post by quedigg on 2006-06-25
also please check this , i got that when i ran the command of your :
"Package `xserver-xrog' is not installed and no info is available."
many thanks!

---

### Post by taurus on 2006-06-25
Sorry.  It's a typo.  I had it right in the first post...
```

sudo dpkg-reconfigure xserver-xorg

```

---

