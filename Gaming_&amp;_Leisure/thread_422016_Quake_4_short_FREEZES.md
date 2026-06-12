---
title: "Quake 4 short FREEZES"
date: 2007-04-24
forum: Gaming &amp; Leisure
---

### Post by Inigo Montoya on 2007-04-24
hi,
i recently bought quake 4 (us dvd edition). installation was quite painful because my brand new dvd drive doesn't work properly (need to check this soon) but i finally did it...
the game starts fine; intro is shown; skippin' through the menus no problem. but when i enter the game (single player or own server) i can just play for some seconds and then the game freezes for 5 to 30 seconds in different intervals. it makes me really crazy, especially because i already spent 6 hours searching the web for similar problems/help...
the only hints i found where these lines passed to the console by quake 4 while the freezes occured:
```
missed 42 sound updates
missed 53 sound updates
missed 42 sound updates
...
```
what i tried so far:
[LIST=1]
[*]checked the md5sums of the pak files (they are ok)
[*]reinstalled quake4-linux-1.3-2.x86.run
[*]played savage and unreal tournament (hardware and nvidia driver work nice there...)
[*]set quake 4 to lowest possible settings (still freezes)
[/LIST]

my system:
cpu: some athlon64 whatever ghz
video: geforce 4 4200
ram: 1gb
linux: kubuntu 7.04
nvidia driver: 9631 (the one that comes with 7.04)

thanks in advance!

im

---

### Post by Inigo Montoya on 2007-04-24
well...
[LIST=1]
[*]i tried setting
```
Option "UseEvents" "false"
``` in the device section of /etc/X11/xorg.conf (X restart required)
[http://www.nvnews.net/vbulletin/showthread.php?t=86253](http://www.nvnews.net/vbulletin/showthread.php?t=86253)
didn't work...
[*]i tried the suggestion in [http://www.nvnews.net/vbulletin/showpost.php?p=1222001&postcount=67](http://www.nvnews.net/vbulletin/showpost.php?p=1222001&postcount=67)
which boils down to
```
modprobe nvidia NVreg_RegistryDwords="PerfLevelSrc=0x2222"
```
didn't work
[/LIST]
:-(

---

### Post by noerrorsfound on 2007-04-24
I had this same problem with the Quake 4 demo. I also have AMD 64, so maybe this is a 64 bit issue? I was running 64 bit Ubuntu also.

---

### Post by Inigo Montoya on 2007-04-25
i discovered the following log message(s) in my /var/log/kernel.log
```
NVRM: Xid (0001:00): 8, Channel 00000002
```
it always appears when quake 4 freezes.
could you check if you have these messages too?
what video card do you use (nvidia or ati)?
btw. in some cases artifacts appear all over the screen when the freezes start. this would lead me to believe its an overheating issue. but the video card works perfectly while playing savage!?
nevertheless i will try another card to see if its harware related...

---

### Post by Inigo Montoya on 2007-04-25
Just found some infos on the Xid message:
[http://forums.nvidia.com/index.php?showtopic=30575&pid=186928&st=0&#](http://forums.nvidia.com/index.php?showtopic=30575&pid=186928&st=0&#)
> Q. My kernel log contains messages that are prefixed with "Xid"; what do these
  messages mean?

A. "Xid" messages indicate that a general GPU error occurred, most often due
  to the driver misprogramming the GPU or to corruption of the commands sent
  to the GPU. These messages provide diagnostic information that can be used
  by NVIDIA to aid in debugging reported problems.

a general GPU error occured... why is it just occuring in quake!?
[http://www.nvnews.net/vbulletin/showthread.php?t=76805](http://www.nvnews.net/vbulletin/showthread.php?t=76805) suggests to set the noapic kernel parameter.
i'll give this a try during the weekend.

im

---

### Post by Inigo Montoya on 2007-04-27
played savage yesterday and the strange short time freeze happend there too but just once after ~1 hour of playing.
i exchanged my grafic card with a geforce fx5200 and tested quake4. although that card seems to be broken somehow too quake 4 worked i.e. no freezes.
_so my problem is hardware (grafic card) related._ really weird...
i guess quake 4 is the **REAL** challenge in comparison to savage and ut.

---

