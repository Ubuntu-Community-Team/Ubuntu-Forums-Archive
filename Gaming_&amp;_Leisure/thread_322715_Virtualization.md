---
title: "Virtualization"
date: 2006-12-20
forum: Gaming &amp; Leisure
---

### Post by jamiekao526 on 2006-12-20
Hey, I was wondering, which virtualization is better suited for gaming under linux?

wine
cedega
xen
qemu
vmware

others?

I'm looking forward to running online mmorpgs like knight online or rapplez.

---

### Post by Wall86 on 2006-12-20
ok, wine i think is about the easiest, cheapest (free)

cedega is made for gaming, but i think a monthly fee apply's

VMWare, DO NOT USE FOR GAMING, problem with vmware is that it is an emulator, you have ubuntu loaded into memory, then you also have windows xp loaded into memory, so if ya really wanna play a game, you will be crawling.

for what i have seen and read, wine is your best bet. Plus there are a ton of HOWTo's out there for wine.

---

### Post by enopepsoo on 2006-12-21
> **Wall86 said:**
> ok, wine i think is about the easiest, cheapest (free)

cedega is made for gaming, but i think a monthly fee apply's

VMWare, DO NOT USE FOR GAMING, problem with vmware is that it is an emulator, you have ubuntu loaded into memory, then you also have windows xp loaded into memory, so if ya really wanna play a game, you will be crawling.

for what i have seen and read, wine is your best bet. Plus there are a ton of HOWTo's out there for wine.

VMWare does have an experimental 3d mode these days.  

I personally love vmware, but it is not free software.  I would suggest that you do not use Qemu to run any games (unless you want old dos games).  Qemu actually emulates a whole processor when it emulates.  VmWare runs as much code directly on the processor as it safely can.

edit: Xen might be fun to try.  It should work.  I have heard bad things about virtualizing XP using Xen (you need a proc with virtualization technology, like a new Xeon, and then it can only run on one of the cores.)  It certainly would be fun to try though!  p.s. I haven't tried this either, I just read it on a couple of blogs (which may have been splogs)

Wine won't work with the newest games because those require a valid copy of Windows so that you can install Direct X.  (Windows Genuine Advantage is just about the exact opposite of apt-get).  They make you do that so that you will buy vista ($300 usd I believe).

Maybe some games will use OpenGL though?  the hell if I know.

---

### Post by jamiekao526 on 2006-12-21
Thanks for the reply.

but qemu is exactly like vmware, (it has an acceleration model called kqemu) except it uses less memory for some odd reason and is slightly harder to use. 

I'll try wine, does cedega offer trial for... trial?

rapplez only uses direct3d


Edit: I tried installing xen... it work to the point where it boots, then it detected my usb mouse and froze. So I don't know what to do... where do I post for help like this?

> **enopepsoo said:**
> 
edit: Xen might be fun to try.  It should work.  I have heard bad things about virtualizing XP using Xen (you need a proc with virtualization technology, like a new Xeon, and then it can only run on one of the cores.)  It certainly would be fun to try though!  p.s. I haven't tried this either, I just read it on a couple of blogs (which may have been splogs) 

O well, most games nowadays only works with one cpu anyways.

---

### Post by enopepsoo on 2006-12-21
> **jamiekao526 said:**
> Thanks for the reply.

but qemu is exactly like vmware, (it has an acceleration model called kqemu) except it uses less memory for some odd reason and is slightly harder to use. 

I'll try wine, does cedega offer trial for... trial?

rapplez only uses direct3d


Edit: I tried installing xen... it work to the point where it boots, then it detected my usb mouse and froze. So I don't know what to do... where do I post for help like this?



O well, most games nowadays only works with one cpu anyways.

kqemu is the kernel module and is much faster than qemu.  I had not thought of that though, sorry.  It probably is as fast as vmware.

qemu is a more nerdier way to virtualize.  It is damn slow though.  Even win98 runs slow on that.](*,)

---

