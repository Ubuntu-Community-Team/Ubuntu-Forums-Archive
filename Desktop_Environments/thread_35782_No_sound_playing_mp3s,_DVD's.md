---
title: "No sound playing mp3s, DVD's"
date: 2005-05-20
forum: Desktop Environments
---

### Post by testingubuntu on 2005-05-20
I have the systems sounds working but any applications that uses the sound card wont output anything 

xmms  
vlc 
mplayer 
totum   
all of the above won't produce any sound

---

### Post by f.prisson on 2005-05-20
Did you set the correct sound daemon in these applications?

---

### Post by testingubuntu on 2005-05-20
Which would be... 

Xmms  esound plugin  Works !

Mplayer 

VLC palyer ?? not to sure about 

Here is lspci... 
> jim@jNOTEBOOK:~$ lspci
0000:00:00.0 Host bridge: Intel Corp. 82852/855GM Host Bridge (rev 02)
0000:00:00.1 System peripheral: Intel Corp. 855GM/GME GMCH Memory I/O Control Registers (rev 02)
0000:00:00.3 System peripheral: Intel Corp. 855GM/GME GMCH Configuration Process Registers (rev 02)
0000:00:02.0 VGA compatible controller: Intel Corp. 82852/855GM Integrated Graphics Device (rev 02)
0000:00:02.1 Display controller: Intel Corp. 82852/855GM Integrated Graphics Device (rev 02)
0000:00:1d.0 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 83)
0000:00:1f.0 ISA bridge: Intel Corp. 82801DBM LPC Interface Controller (rev 03)
0000:00:1f.1 IDE interface: Intel Corp. 82801DBM (ICH4) Ultra ATA Storage Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
0000:00:1f.6 Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
0000:01:01.0 Network controller: Intel Corp. PRO/Wireless 2200BG (rev 05)
0000:01:02.0 Ethernet controller: VIA Technologies, Inc. VT6105 [Rhine-III] (rev 8b)
0000:01:03.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02) 


Which audio driver Should I use? 
Where does this audio deamon lurk... 

here is ps -A 
> 
jim@jNOTEBOOK:~$ ps -A
  PID TTY          TIME CMD
    1 ?        00:00:00 init
    2 ?        00:00:00 ksoftirqd/0
    3 ?        00:00:00 events/0
    4 ?        00:00:00 khelper
   22 ?        00:00:00 kacpid
  113 ?        00:00:00 kblockd/0
  148 ?        00:00:00 pdflush
  149 ?        00:00:00 pdflush
  151 ?        00:00:00 aio/0
  150 ?        00:00:01 kswapd0
  738 ?        00:00:00 kseriod
 1108 ?        00:00:00 kjournald
 1135 ?        00:00:00 udevd
 3180 ?        00:00:00 kjournald
 3181 ?        00:00:00 kjournald
 3903 ?        00:00:00 khubd
 6198 ?        00:00:00 ipw2200/0
 6536 ?        00:00:00 pccardd
 6846 ?        00:00:00 dhclient3
 7196 ?        00:00:00 syslogd
 7226 ?        00:00:00 dd
 7228 ?        00:00:00 klogd
 7262 ?        00:00:00 gdm
 7272 ?        00:00:00 gdm
 7307 ?        00:01:16 Xorg
 7313 ?        00:00:00 cupsd
 7912 ?        00:00:00 acpid
 7974 ?        00:00:00 dbus-daemon-1
 7986 ?        00:00:01 hald
 7999 ?        00:00:00 inetd
 8077 ?        00:00:00 cardmgr
 8232 ?        00:00:00 master
 8243 ?        00:00:00 qmgr
 8406 ?        00:00:00 powernowd
 8434 ?        00:00:00 atd
 8445 ?        00:00:00 cron
 8467 tty1     00:00:00 getty
 8468 tty2     00:00:00 getty
 8469 tty3     00:00:00 getty
 8470 tty4     00:00:00 getty
 8471 tty5     00:00:00 getty
 8472 tty6     00:00:00 getty
 8569 ?        00:00:00 x-session-manag
 8614 ?        00:00:00 ssh-agent
 8617 ?        00:00:00 dbus-launch
 8618 ?        00:00:00 dbus-daemon-1
 8620 ?        00:00:01 gconfd-2
 8623 ?        00:00:00 gnome-keyring-d
 8625 ?        00:00:01 esd
 8627 ?        00:00:00 bonobo-activati
 8629 ?        00:00:00 gnome-settings-
 8632 ?        00:00:00 gam_server
 8640 ?        00:00:00 xscreensaver
 8664 ?        00:00:00 gnome-smproxy
 8666 ?        00:00:03 metacity
 8668 ?        00:00:02 gnome-panel
 8670 ?        00:00:00 gnome-volume-ma
 8672 ?        00:00:02 nautilus
 8674 ?        00:00:00 update-notifier
 8680 ?        00:00:12 engage
 8682 ?        00:00:00 gnome-cups-icon
 8684 ?        00:00:00 evolution-alarm
 8687 ?        00:00:00 gnome-vfs-daemo
 8697 ?        00:00:00 mapping-daemon
 8712 ?        00:00:00 cpufreq-applet
 8715 ?        00:00:00 evolution-data-
 8725 ?        00:00:00 clock-applet
 8727 ?        00:00:00 trashapplet
 8729 ?        00:00:01 gnome-netstatus
 8731 ?        00:00:03 mixer_applet2
 9901 ?        00:01:12 firefox-bin
10329 ?        00:00:00 pickup
10675 ?        00:00:01 multiload-apple
10692 ?        00:00:02 gnome-terminal
10693 ?        00:00:00 gnome-pty-helpe
10694 pts/0    00:00:00 bash
10736 pts/0    00:00:00 ps

---

### Post by logan2004 on 2005-05-20
any difference when you got to System > Preferences >  Sound 

and uncheck "Enable Sound Server Startup" ?

---

### Post by testingubuntu on 2005-05-20
[QUOTE=logan2004]any difference when you got to System > Preferences >  Sound 

and uncheck "Enable Sound Server Startup" ?[/QUOTE]


That did it ! 

Thanks  

There are so many differences between Fedora Core & Ubuntu

---

### Post by whetherornot on 2005-05-20
I did the same thing (disable sound server startup), and it worked, so thanks logan2004.

I  want to know what sound server VLC is using when it's playing sound. ESD has been killed, and I'm not running JACK. There is not output from ls /dev/dsp or ls /dev/snd/*.

Where is the sound coming from? I'm pretty new at understanding what a sound server is, so I'd love to know what's happening.

---

