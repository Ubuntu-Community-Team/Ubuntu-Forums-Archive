---
title: "Dell V-505 AIO Printer on Ubuntu 10.10"
date: 2011-01-31
forum: Dell Ubuntu Support (CLOSED)
---

### Post by FrankenCub on 2011-01-31
Has anyone found a way to use the V-505 printer with 10.10 ? I use my printer a Lot and can get away with booting in Windows for now but I'm gonna building a new computer soon and it will not be duel boot. I'm goin with Ubuntu exclusively for the new one. I don't really want to replace the printer, it's pretty new yet lol.

---

### Post by anglican on 2011-01-31
> **FrankenCub said:**
> Has anyone found a way to use the V-505 printer with 10.10 ? I use my printer a Lot and can get away with booting in Windows for now but I'm gonna building a new computer soon and it will not be duel boot. I'm goin with Ubuntu exclusively for the new one. I don't really want to replace the printer, it's pretty new yet lol.There are drivers for 8.04 which you can get from either Dell or Lexmark (the equivalent model is the Lexmark X5650). Try installing these (I'd go for the Lexmark site) and report back success/failure.

H

---

### Post by FrankenCub on 2011-01-31
Thanks for the tip. I went to Lexmark and they didn't have the 8.04 driver so I downloaded the 10.04 driver. When I try to open it in terminal I get an error...
[INDENT]Lua error detected: While parsing install.lua: install.lua:118: Overflow detected: Not enough space for widget.[/INDENT]

What does this mean ? I have 8Gb free so I know I have enough room :confused:

---

### Post by anglican on 2011-02-01
> **FrankenCub said:**
> Thanks for the tip. I went to Lexmark and they didn't have the 8.04 driver so I downloaded the 10.04 driver. When I try to open it in terminal I get an error...
[INDENT]Lua error detected: While parsing install.lua: install.lua:118: Overflow detected: Not enough space for widget.[/INDENT]

What does this mean ? I have 8Gb free so I know I have enough room :confused:The following works for me on my 32-bit install:
Download file:

```
wget http://downloads.lexmark.com/downloads/cpd/lexmark-08z-series-driver-1.0-1.i386.deb.sh.tar.gz
```Untar it with:
```
tar xvfz lexmark-08z-series-driver-1.0-1.i386.deb.sh.tar.gz
```become root (administrator privileges are needed for the next step)
```
sudo bash
```Finally run the installer:
```
./lexmark-08z-series-driver-1.0-1.i386.deb.sh
```... but are you running a 64-bit OS, in which case expect problems!

H

---

### Post by FrankenCub on 2011-02-01
Hmmm...thanks. I just tried that and it still gives me the same error....
not enough space for widget

This is what shows at the terminal...

Collecting info for this system...
Operating system: linux
CPU Arch: x86
TRACKING IDENT = 170209
cpu speed = 2660 MHz
ram size = 2002.94140625 MB
hd avail = 2155 MB
root@brendan-OptiPlex-210L:~#

Oh, 32bit by the way.

---

### Post by anglican on 2011-02-02
> **FrankenCub said:**
> Hmmm...thanks. I just tried that and it still gives me the same error....
not enough space for widget

This is what shows at the terminal...

Collecting info for this system...
Operating system: linux
CPU Arch: x86
TRACKING IDENT = 170209
cpu speed = 2660 MHz
ram size = 2002.94140625 MB
hd avail = 2155 MB
root@brendan-OptiPlex-210L:~#

Oh, 32bit by the way.OK it looks like you're not the first to have this problem. There appears to be a solution at:

[http://art.ubuntuforums.org/showthread.php?t=1634491&page=2](http://art.ubuntuforums.org/showthread.php?t=1634491&page=2)

Take a look at message #15. Note that you will have to use the filenames appropriate for the driver you want to install. Let us know if it works for you too.

i.e.
```

sudo sh lexmark-08z-series-driver-1.0-1.i386.deb.sh --noexec --target temp
cd temp
sudo tar xvvf instarchive_all --lzma
sudu dpkg -i lexmark-08z-series-driver-1.0-1.i386.deb

```

H

---

### Post by FrankenCub on 2011-02-02
> **anglican said:**
> OK it looks like you're not the first to have this problem. There appears to be a solution at:

[http://art.ubuntuforums.org/showthread.php?t=1634491&page=2](http://art.ubuntuforums.org/showthread.php?t=1634491&page=2)

Take a look at message #15. Note that you will have to use the filenames appropriate for the driver you want to install. Let us know if it works for you too.
H

I saw that topic before I posted this topic. There were a couple other topics that were kinda dealing with the same issues too.
That one didn't work either. It's weird, no matter what I do the Lexmark drivers will not load for anything. I tried the Dell drivers also before posting for help. The have one for 8.04. The Dell drivers wouldn't load either.

After looking through the tips/instruction that you gave me I decided to try those with the Dell driver, loaded fine the first time. It recognized the printer and model immediately and has worked well with the few different pages I printed. 

Thanks a ton for the help with this, it is much appreciated ;)
This is just experimental on this computer, this way I'll have the bugs worked out when I build a new computer....very soon I hope. This one has to be near the end of it's life lol.

Thanks again Anglican !

---

