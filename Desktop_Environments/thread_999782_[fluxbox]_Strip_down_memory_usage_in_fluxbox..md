---
title: "[fluxbox] Strip down memory usage in fluxbox."
date: 2008-12-02
forum: Desktop Environments
---

### Post by rakris on 2008-12-02
I am fairly new to fluxbox though not to linux.
In current installation i had used kde, gnome and xfce.

My memory consumption goes to 200MB. I am having 1GB ram. I want to strip it down as much as possible.
So let me tel you guys what applications I usually run in my system so that you can advise what and what not to run.

Browser-Firefox (using gtk-theme-switch)
deluge-torrent (Any other alternative ??? to be less resource hungry. I know about transmissioncli, but it does not have feature to select specific files in a mutli file torrent)
RhythmBox (alternative??)
gnome-terminal (Any light terminal with good UI like this?)
games like xmoto, padman, smc
smplayer (Sometimes, most of the time i use commandline mplayer).
Openoffice.

Also i think background daemon  apps are consuming more memory.
here is my output of ps -e.


```

krish@krish-laptop:~/.fluxbox$ ps -e
  PID TTY          TIME CMD
    1 ?        00:00:02 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 migration/1
    7 ?        00:00:00 ksoftirqd/1
    8 ?        00:00:00 watchdog/1
    9 ?        00:00:00 events/0
   10 ?        00:00:00 events/1
   11 ?        00:00:00 khelper
   51 ?        00:00:00 kintegrityd/0
   52 ?        00:00:00 kintegrityd/1
   54 ?        00:00:00 kblockd/0
   55 ?        00:00:00 kblockd/1
   57 ?        00:00:00 kacpid
   58 ?        00:00:00 kacpi_notify
  145 ?        00:00:00 cqueue
  149 ?        00:00:00 kseriod
  194 ?        00:00:00 pdflush
  195 ?        00:00:00 pdflush
  196 ?        00:00:00 kswapd0
  238 ?        00:00:00 aio/0
  239 ?        00:00:00 aio/1
 1223 ?        00:00:00 ksuspend_usbd
 1224 ?        00:00:00 khubd
 1298 ?        00:00:00 khpsbpkt
 1349 ?        00:00:00 ata/0
 1355 ?        00:00:00 ata/1
 1358 ?        00:00:00 ata_aux
 2039 ?        00:00:00 scsi_eh_0
 2040 ?        00:00:01 scsi_eh_1
 2053 ?        00:00:00 knodemgrd_0
 2215 ?        00:00:01 kjournald
 2389 ?        00:00:00 udevd
 2570 ?        00:00:00 kmmcd
 2587 ?        00:00:00 pccardd
 2847 ?        00:00:00 kpsmoused
 2911 ?        00:00:00 iwl3945/0
 2912 ?        00:00:00 iwl3945/1
 2931 ?        00:00:00 iwl3945
 4361 ?        00:00:00 kjournald
 4720 tty4     00:00:00 getty
 4721 tty5     00:00:00 getty
 4729 tty2     00:00:00 getty
 4730 tty3     00:00:00 getty
 4731 tty6     00:00:00 getty
 4906 ?        00:00:00 acpid
 4946 ?        00:00:00 kondemand/0
 4948 ?        00:00:00 kondemand/1
 5030 ?        00:00:00 syslogd
 5080 ?        00:00:00 dd
 5082 ?        00:00:00 klogd
 5106 ?        00:00:03 dbus-daemon
 5128 ?        00:00:00 avahi-daemon
 5129 ?        00:00:00 avahi-daemon
 5188 ?        00:00:00 mysqld_safe
 5230 ?        00:00:01 mysqld
 5231 ?        00:00:00 logger
 5334 ?        00:00:00 cupsd
 5541 ?        00:00:02 hald
 5544 ?        00:00:00 console-kit-dae
 5545 ?        00:00:00 hald-runner
 5627 ?        00:00:00 hald-addon-inpu
 5642 ?        00:00:00 hald-addon-cpuf
 5643 ?        00:00:00 hald-addon-acpi
 5665 ?        00:00:01 hald-addon-stor
 5697 ?        00:00:00 bluetoothd
 5704 ?        00:00:00 btaddconn
 5705 ?        00:00:00 btdelconn
 5736 ?        00:00:00 krfcommd
 5759 ?        00:00:00 NetworkManager
 5769 ?        00:00:00 wpa_supplicant
 5771 ?        00:00:00 nm-system-setti
 5801 ?        00:00:00 gdm
 5804 ?        00:00:00 gdm
 5807 tty7     00:03:16 Xorg
 5828 ?        00:00:00 system-tools-ba
 5863 ?        00:00:00 atd
 5891 ?        00:00:00 cron
 5994 tty1     00:00:00 getty
 6046 ?        00:00:00 gnome-keyring-d
 6057 ?        00:00:07 fluxbox
 6123 ?        00:00:00 dbus-launch
 6124 ?        00:00:00 dbus-daemon
 6127 ?        00:00:00 xscreensaver
 6168 ?        00:00:00 bonobo-activati
 6173 ?        00:00:00 gvfsd
 6179 ?        00:00:00 gvfs-fuse-daemo
 6294 ?        00:00:00 xfce-mcs-manage
 6604 ?        00:00:48 gnome-terminal
 6606 ?        00:00:00 gconfd-2
 6609 ?        00:00:00 gnome-pty-helpe
 6610 pts/1    00:00:00 bash
 7480 ?        00:05:25 firefox
 7785 ?        00:00:20 deluge
 7795 ?        00:00:00 gvfs-hal-volume
 7797 ?        00:00:00 gvfs-gphoto2-vo
 7799 ?        00:00:02 trackerd
 7810 ?        00:00:05 deluged
12256 pts/1    00:00:00 ps
krish@krish-laptop:~/.fluxbox$ 



```
What the hell are those K apps.? I dont know which all services i should remove. Can you guys help me with these 2 problems..

---

### Post by Izek on 2008-12-02
Have you tried swiftfox? ( [http://getswiftfox.com/](http://getswiftfox.com/) )

As for openOffice, what do you use in OpenOffice? If you just use the word processor, might I suggest using AbiWord? Granted, AbiWord doesn't have support for Small Caps.

---

### Post by snowpine on 2008-12-02
You are only using 20% of your ram; I wouldn't worry about it! :)
Linux is very clever in its use of ram. If you have lots of ram, it will use caching and other tricks to boost performance. If you want to try an experiment, take one of your ram sticks out (if possible) so you only have 512mb. Run the exact same applications, and I bet you will see less than 200mb used...

---

### Post by Izek on 2008-12-02
> **snowpine said:**
> Linux is very clever in its use of ram.

I wish it was that clever in CPU usage.

102% :lolflag:

---

### Post by lswest on 2008-12-02
Well, the only thing I would suggest is rxvt-unicode as a terminal.  Text file config only though, so it may not be for you.  If you want, PM me and I can send you my config file.

Apart from that I agree with what was said earlier.

---

### Post by rakris on 2008-12-02
Thanks guys.

I know my RAM is very huge to accomodate all junk applications. 
But I feel restless and sleepless if i dont remove those unwanted services from init.d :)

Are those K apps from KDE from my previous installation? is it safe to remove all of them?

And I will try Abiword and rxvt..

---

### Post by rakris on 2008-12-14
Wow. I was just googling memory utilization in fluxbox and guess what? My topic came first.

The problem is solved now.

I removed all the gnome specific apps. (check psychocats.net for package list). 
I removed nvidia driver. Using opensource 'nv' driver instead.

Result: Memory used 160, cached **60** MB


Cheers............

---

### Post by hictio on 2008-12-14
Regarding the Bit Torrent client, give [ctorrent](http://ctorrent.sourceforge.net/) a try.
I have used it extensively on OpenBSD on a box with a 233MHz CPU and 128 MB of RAM, the little program performed excellent.

---

### Post by Izek on 2008-12-14
> **hictio said:**
> Regarding the Bit Torrent client, give [ctorrent](http://ctorrent.sourceforge.net/) a try.
I have used it extensively on OpenBSD on a box with a 233MHz CPU and 128 MB of RAM, the little program performed excellent.

All of the page links still show the home page content, IE [http://ctorrent.sourceforge.net/?action=faq](http://ctorrent.sourceforge.net/?action=faq)

---

### Post by urukrama on 2008-12-14
> **rakris said:**
> Browser-Firefox (using gtk-theme-switch)
deluge-torrent (Any other alternative ??? to be less resource hungry. I know about transmissioncli, but it does not have feature to select specific files in a mutli file torrent)
RhythmBox (alternative??)
gnome-terminal (Any light terminal with good UI like this?)
games like xmoto, padman, smc
smplayer (Sometimes, most of the time i use commandline mplayer).
Openoffice.


Try urxvt (rxvt-unicode) as a terminal or alternatively Sakura or even Xfce4-terminal. 

Rtorrent is the best and lightest torrent client around, though it is a command-line application. 

Try audacious, mpd + gmpc or sonata, or cplay or mocp (command-line players) to play audio files.

Mplayer without a GUI is the lightest and most feature rich video player.

Opera is faster and lighter than Firefox, especially if you configure it properly.

---

### Post by hictio on 2008-12-14
> **Izek said:**
> All of the page links still show the home page content, IE [http://ctorrent.sourceforge.net/?action=faq](http://ctorrent.sourceforge.net/?action=faq)

Oh, yeah, so it seems you have to use the [Enhanced CTorrent](http://www.rahul.net/dholmes/ctorrent/) one, now with more Torrent! ;)

---

### Post by Izek on 2008-12-14
> **hictio said:**
> Oh, yeah, so it seems you have to use the [Enhanced CTorrent](http://www.rahul.net/dholmes/ctorrent/) one, now with more Torrent! ;)

Ubuntu is lame:
```
ian@ian-desktop:~/Desktop/ctorrent-dnh3.3.2$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking for C++ compiler default output file name... 
configure: error: C++ compiler cannot create executables
See `config.log' for more details.
ian@ian-desktop:~/Desktop/ctorrent-dnh3.3.2$ make install
make: *** No rule to make target `install'.  Stop.

```

---

### Post by hictio on 2008-12-14
> **Izek said:**
> Ubuntu is lame:
```
ian@ian-desktop:~/Desktop/ctorrent-dnh3.3.2$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking for C++ compiler default output file name... 
configure: error: C++ compiler cannot create executables
See `config.log' for more details.
ian@ian-desktop:~/Desktop/ctorrent-dnh3.3.2$ make install
make: *** No rule to make target `install'.  Stop.

```


AFAIK, you can install it directly using aptitude.

---

### Post by Izek on 2008-12-14
is the name of the package simply ctorrent?

---

### Post by hictio on 2008-12-14
Yeap.
Are you going to give it a try?

---

### Post by Izek on 2008-12-14
> **hictio said:**
> Yeap.
Are you going to give it a try?

Wow, a whole 2.x.x versions behind in synaptic! >>;

I don't know about this.

---

### Post by hictio on 2008-12-14
I don't recall which version I was running on OpenBSD :(
But, I remember I have installed it via pkg_add.

---

### Post by rakris on 2008-12-15
thanks guys.
But I am already using Xterm, rtorrent and no file manager :) mplayer-nogui.

Thats how I did it

---

