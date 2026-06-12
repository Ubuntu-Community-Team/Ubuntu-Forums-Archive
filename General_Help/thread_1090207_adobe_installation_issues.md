---
title: "adobe installation issues"
date: 2009-03-08
forum: General Help
---

### Post by r0k on 2009-03-08
when i try to install adobe through a terminal i get errors 
example=
jake@jake-desktop:~$ ~/Desktop
bash: /home/jake/Desktop: is a directory
jake@jake-desktop:~$ cd ~/Desktop
jake@jake-desktop:~/Desktop$ chmod +x adobe-release-i386-1.0-1.noarch.rpm
jake@jake-desktop:~/Desktop$ sudo ./adobe-release-i386-1.0-1.noarch.rpm
[sudo] password for jake: 
./adobe-release-i386-1.0-1.noarch.rpm: 1: Syntax error: ")" unexpected
jake@jake-desktop:~/Desktop$ 


please and thank you!

---

### Post by dzark on 2009-03-08
you've got yourself a .rpm file which is the installer for RedHat linux flavours... 

what type of adobe are you trying to install? there's easier ways....

---

### Post by r0k on 2009-03-08
adobe flash player

---

### Post by dzark on 2009-03-08
try this one

```
sudo aptitude install ubuntu-restricted-extras
```

flash player/dvd decoder/mp3 etc all in the one hit :) nice and easy

---

### Post by r0k on 2009-03-08
thank you!

---

### Post by taurus on 2009-03-08
You cannot install .rpm the way you are doing.  It's not the same thing as you installed RealPlayer11GOLD.bin.

If you want to install flash plugin, it's in the repos.

```
sudo apt-get update
sudo apt-get install flashplugin-nonfree
```
And if you want to install adobe reader--acroread, add Medibuntu to your repos and install it from there.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by r0k on 2009-03-08
i tried that and got this!!

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
jake@jake-desktop:~$ sudo apt-get install flashplugin-nonfree
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by taurus on 2009-03-08
Do you have update manager, add/remove, or synaptic open right now?  If you do, you must close it first before you can run apt-get from a terminal.

---

### Post by dzark on 2009-03-08
you can only run one installer at a time..

if you still got synaptic/update-manager open you could just browse to the 'ubuntu-restricted-extras' package from there..

---

### Post by r0k on 2009-03-08
im pretty sure nothing else is running!  i dont know how to check running processes either though! i guess somthing could be running in the background! how can i check?

---

### Post by dzark on 2009-03-08
```
ps -A
``` will list All of the _p_roce_s_ses

have a look for dpkg or apt-somethingoroother

---

### Post by r0k on 2009-03-08
16634 pts/2    00:00:00 dpkg
jake@jake-desktop:~$ ps -A
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 events/0
    7 ?        00:00:00 khelper
   46 ?        00:00:00 kintegrityd/0
   48 ?        00:00:00 kblockd/0
   50 ?        00:00:00 kacpid
   51 ?        00:00:00 kacpi_notify
  163 ?        00:00:00 cqueue
  167 ?        00:00:00 kseriod
  208 ?        00:00:00 pdflush
  209 ?        00:00:00 pdflush
  210 ?        00:00:00 kswapd0
  252 ?        00:00:00 aio/0
 1317 ?        00:00:00 ksuspend_usbd
 1323 ?        00:00:00 khubd
 1340 ?        00:00:00 ata/0
 1344 ?        00:00:00 ata_aux
 1347 ?        00:00:00 khpsbpkt
 2101 ?        00:00:00 knodemgrd_0
 2104 ?        00:00:00 scsi_eh_0
 2107 ?        00:00:00 scsi_eh_1
 2138 ?        00:00:00 scsi_eh_2
 2139 ?        00:00:00 scsi_eh_3
 2146 ?        00:00:00 scsi_eh_4
 2147 ?        00:00:00 scsi_eh_5
 2257 ?        00:00:00 kjournald
 2431 ?        00:00:00 udevd
 2607 ?        00:00:00 kgameportd
 2801 ?        00:00:00 rt2500usb
 3071 ?        00:00:00 kpsmoused
 4307 tty4     00:00:00 getty
 4308 tty5     00:00:00 getty
 4315 tty2     00:00:00 getty
 4316 tty3     00:00:00 getty
 4317 tty6     00:00:00 getty
 4492 ?        00:00:00 acpid
 4539 ?        00:00:00 kondemand/0
 4609 ?        00:00:00 syslogd
 4664 ?        00:00:00 dd
 4666 ?        00:00:00 klogd
 4689 ?        00:00:00 dbus-daemon
 4711 ?        00:00:00 avahi-daemon
 4712 ?        00:00:00 avahi-daemon
 4755 ?        00:00:00 cupsd
 4913 ?        00:00:00 hald
 4916 ?        00:00:00 console-kit-dae
 4979 ?        00:00:00 hald-runner
 5000 ?        00:00:00 hald-addon-inpu
 5014 ?        00:00:00 hald-addon-acpi
 5070 ?        00:00:00 bluetoothd
 5075 ?        00:00:00 btaddconn
 5077 ?        00:00:00 btdelconn
 5097 ?        00:00:00 krfcommd
 5125 ?        00:00:00 NetworkManager
 5129 ?        00:00:00 wpa_supplicant
 5132 ?        00:00:00 nm-system-setti
 5163 ?        00:00:00 gdm
 5166 ?        00:00:00 gdm
 5170 tty7     00:02:24 Xorg
 5187 ?        00:00:00 system-tools-ba
 5224 ?        00:00:00 atd
 5252 ?        00:00:00 cron
 5330 tty1     00:00:00 getty
 5356 ?        00:00:00 gnome-keyring-d
 5367 ?        00:00:00 x-session-manag
 5549 ?        00:00:00 dbus-launch
 5550 ?        00:00:00 dbus-daemon
 5553 ?        00:00:00 pulseaudio
 5558 ?        00:00:00 gconf-helper
 5560 ?        00:00:02 gconfd-2
 5566 ?        00:00:00 seahorse-agent
 5569 ?        00:00:00 gvfsd
 5570 ?        00:00:00 gnome-keyring-d
 5575 ?        00:00:02 gnome-settings-
 5576 ?        00:00:00 compiz
 5586 ?        00:00:00 gvfs-fuse-daemo
 5652 ?        00:00:08 gnome-screensav
 5655 ?        00:01:23 compiz.real
 5656 ?        00:00:00 sh
 5657 ?        00:00:00 compiz-decorato
 5659 ?        00:00:05 gtk-window-deco
 5660 ?        00:00:11 gnome-panel
 5661 ?        00:00:10 nautilus
 5664 ?        00:00:00 bonobo-activati
 5672 ?        00:00:00 gvfs-hal-volume
 5674 ?        00:00:00 gvfs-gphoto2-vo
 5678 ?        00:00:00 trashapplet
 5681 ?        00:00:00 gvfsd-trash
 5687 ?        00:00:00 gvfsd-burn
 5690 ?        00:00:00 fast-user-switc
 5693 ?        00:00:00 mixer_applet2
 5708 ?        00:00:01 update-notifier
 5709 ?        00:00:00 tracker-applet
 5710 ?        00:00:00 trackerd
 5712 ?        00:00:01 nm-applet
 5713 ?        00:00:00 python
 5721 ?        00:00:00 evolution-alarm
 5724 ?        00:00:00 bluetooth-apple
 5727 ?        00:00:00 gnome-power-man
 5729 ?        00:00:00 dhclient
 5736 ?        00:00:00 evolution-data-
 5740 ?        00:00:00 evolution-excha
 5771 ?        00:00:01 notification-da
16512 ?        00:00:01 aptitude
16634 pts/2    00:00:00 dpkg
16651 pts/2    00:00:00 frontend
16658 pts/2    00:00:00 preinst
16660 pts/2    00:00:00 whiptail
16711 ?        00:00:33 firefox
16905 ?        00:00:01 jockey-backend
17249 ?        00:00:00 gnome-terminal
17251 ?        00:00:00 gnome-pty-helpe
17252 pts/0    00:00:00 bash
17270 pts/0    00:00:00 ps

---

### Post by r0k on 2009-03-08
wow im so new!! lol!!!  this is so confusing to me!  linux users have to be way smarter then windows users

---

### Post by r0k on 2009-03-08
ok so i restarted my computer and tried taurus's method and got this error

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
jake@jake-desktop:~$ sudo apt-get install flashplugin-nonfree
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
so i then tried!!!
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
jake@jake-desktop:~$ dpkg --configure -a

and got this

dpkg: requested operation requires superuser privilege

---

### Post by r0k on 2009-03-08
woohoo figured it out on my own!! i needed to use the sudo code

---

### Post by dzark on 2009-03-08
congrats bro!

once you get the hang of it, it kinda starts making a lot more sense than windows... you know you want something, even if you've never seen it before you know where to look and you'll find something that can do it.. i did a gig a few weeks back where i needed a video played with a countdown timer in a particular spot (because of texts/logos etc).. windows would've been quite the mission, maybe pre-rendereing and all that, in linux it was 10 minutues with a python script... they guy standing behind me couldnt' believe it.. 

by the looks of it you've got compiz running? wobbly windows & transparencies? thumbnails in the taskbar.. no turnin back for you now!hah

also check out amarok music player.. get the old (1.4 one - 2.0's still got a bit to come yet) runs circles around WMP/iTunes..

---

