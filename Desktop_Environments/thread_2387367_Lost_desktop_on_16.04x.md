---
title: "Lost desktop on 16.04x"
date: 2018-03-15
forum: Desktop Environments
---

### Post by ubuntubrian on 2018-03-15
OK, this is weird as I have the same problem, I think. I ran a normal Update manager update and after restarting the problem occurred. No desktop GUI. I get the following which I've edited way down as there's too much to type here.
All in booting which opens text mode.

Try to startx and it fails with "connection to X server lost"

I've investigated this for hours and the command

```
$ Who
loginname  tty1   2018-03-14  21:04  
```

There should be a DISPLAY in that query after the time like this:
```
$ Who
loginname  tty1   2018-03-14  21:04  (:0.0)
```

The time and date are wrong but that was the time I shut down the machine yesterday but ran 
```
NetworkManager
``` 
and have connectivity and the correct time now
 
So the only dm I can run is lightdm with 
```
sudo lightdm
``` 

But even tho it displays and the cursor works there is nothing usable.

So I've run every single option that I can try from forums on this issue. If I still have a display then it's not being detected. When I try running unity I get several compiz errors similar to yours but the fatal one is

```
WARNING: no DISPLAY variable set, setting it to :0
Compiz (core) - Fatal: couldn't open display :0
```

there are other compiz msgs. but not errors so not included above

Hope this either helps or gets me some help!
Thanx

---

### Post by ubuntubrian on 2018-03-15
Just an update. By setting Display to :0  by Display=:0 export Display I was to launch lightdm tho only as a guest. It's and xfce wm with limited usability. switching to tty I lose the wm and it seems like random efforts to reestablish it sort of work. I must be on some right path here but don't know how to fix the real missing DISPLAY issue.

---

### Post by ubuntubrian on 2018-03-16
Just to clarify, I updated some normal updates as prompted by Update Manager about 3 days ago. I'm 16.04 and they were normal security updates. Now when I boot  the machine starts in graphic mode as (all hand typed and a real pain in the a**!) 
```
ubuntu-laptop login:
```
and I can log in as myself (ubuntu)
```
ubuntu-laptop login: ubuntu
```
```
Password
```
then I try, which has always worked, 
```
ubuntu@ubuntu-laptop: ~$ startx
```
returns
```
X.Org X Server 1.18.4
Release Date 2016-07-19
X Protocol Version 11, Revision 0
Build Operating System: Linux 4.4.0-97-generic x86_64 Ubuntu
Current Operating System: Linux ubuntu-laptop 4.4.0-117-generic #141-Ubuntu SMP Tue Mar 13 11:58:07 UTC 2018 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-117-generic root=UUID=ea9f5446-2b36-4ba1-bcfs-ac786107fd58 ro vga=792 quiet splash acpi_osi=Linux vt.handoff=7
Build Date: 13 October 2017 01:57:05PM
xorg-server 2:1.18.4-0ubuntu0.7
Current version of pixman: 0.33.6
Before reporting problems check http://wiki.x.org
to make sure you have the latest version
Markers: [I]various symbols[I]
(==) Log file: "home/ubuntu/.localshare/xorg/Xorg.1.log" time, (current time)
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
waiting for X server to shut down (II) server terminated successfully (0). Closing log file.esetting enabled.xinit: connection to X server lost
```
So I get no GUI at all with me as user. However, I have a guest user that starts lightdm all by itself if I (ctrl+alt+f7) I can switch to my user in a terminal but the desktop remains lightdm and as guest. Some apps run, like libreoffice, and most do not like firefox, thunderbird, synaptic

---

### Post by plucky on 2018-03-20
[This Post](https://ubuntuforums.org/showthread.php?t=2386528&page=2&p=13747983&viewfull=1#post13747983)

> **buckcw said:**
> Thanks for sharing. It worked for me, or to be precise the rm command worked ;)

[INDENT][FONT=courier new]sudo rm -r ~/.cache[/FONT][/INDENT]

Thanks again!

The above command worked for me.

If you login as normal user and open a terminal ```
ctrl+alt+t
``` you should be able to run the command. Desktop should appear after a reboot.

Good Luck

---

