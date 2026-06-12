---
title: "XFCE not what I expected on a slow machine"
date: 2007-09-06
forum: Desktop Environments
---

### Post by ganja_guru on 2007-09-06
Hi everyone,

I am installing xubuntu on a friends old P III 600 Mhz with 64 MB ram and a 40 GB HDD. Install had a few issues which were worked out, but now I find XFCE to be unbelieveably slow.. Using things like synpatic or gnome-app-manager requires about two minutes everytime I want to MARK a package for installaion. I understand the ram is less, but this performance is impossible to work with. Opening firefox takes about a minute and a half. I'm not able to figure out whats wrong, so please help me out. 

P.S - its not the 'lo' network interface, that seems fine here.

---

### Post by MetalMusicAddict on 2007-09-06
Its the RAM sir. Everything else should do fine.

---

### Post by Lord Illidan on 2007-09-06
64 MB RAM is a bit too little, don't you think? In this situation, I'd try Zenwalk or possibly DSL.

---

### Post by ganja_guru on 2007-09-06
Thanks for the quick replies. Yup RAM is definitely too less for me considering I run 2GB on my primary Desktop :) . I'm only a bit curious as to why it isn't faster considering I've read reviews where people are happy with XFCE on P II/ 64MB ram..

---

### Post by Lord Illidan on 2007-09-06
XFCE is not Xubuntu.
XFCE is just the Desktop Environment. While XFCE is less bloated than Gnome,the Xubuntu core still adds the bulk of Ubuntu. Zenwalk for example has XFCE and less bloat (slackware based).

---

### Post by por100pre1 on 2007-09-06
Some users try strip Xubuntu of all services and processes they can. But IMHO your best bet would be to try DSL or Puppy Linux. Be sure to try them first on CD, just to check if they work with your hardware. :)

---

### Post by mojoman on 2007-09-06
You could try the server install and then add x-server and a good window manager, such as fluxbox. I wouldn't be surprised it that sort of setup would work fairly good on those specs.

---

### Post by RedSquirrel on 2007-09-07
A minimal install might be worth a try:

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)
[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

with Fluxbox or IceWM, for example. There is also the **xfce4** metapackage in the repositiories which installs only a *bare-bones* Xfce. However, with that low RAM I would probably stick with a light window manager. Up to you.

---

### Post by trippinnik on 2007-10-17
you should really check what services are also loaded in the background. Beagle, MySQl, Apache, etc should be turned off.  Also try lightweight versions of similar apps.  In my opinion Firefox really is a problem, it's become very bloated.  I've been using the new Opera alpha and it's fast, but even Mozilla or Galeon are quite fast.  For installing apps, you can use aptitude, either use the CLI or if you don't pass it any commands it has a simple text interface.
Most of the other distros mentioned do similar things, choosing lighterwieght apps etc. So you can subtract or try one of the other distros that focuses on this kind of thing.

---

### Post by TeaSwigger on 2007-10-17
64mb ram? Geez. If it's stuck with that... Might want to seriously consider using command line / terminal apps / utilities when workable. Sure wouldn't try Firefox on that. More like Links2, Elinks, Dillo, or if you really want the rendering Kazehakase at the most. Certainly do the package management by terminal. Aptitude for instance. Not saying "throw the computer away" or "don't use ubuntu" or anything, by all means use and enjoy, but ubuntu and its derivatives are intended for more modern higher-spec units, so you'll have to adapt it and your expectations to work well with the limitiations. :)

---

### Post by disasm on 2007-10-17
> **ganja_guru said:**
> Hi everyone,

I am installing xubuntu on a friends old P III 600 Mhz with 64 MB ram and a 40 GB HDD. Install had a few issues which were worked out, but now I find XFCE to be unbelieveably slow.. Using things like **synpatic or gnome-app-manager requires about two minutes everytime I want to MARK a package **for installaion. I understand the ram is less, but this performance is impossible to work with. Opening firefox takes about a minute and a half. I'm not able to figure out whats wrong, so please help me out. 

P.S - its not the 'lo' network interface, that seems fine here.

Just a note, loading a gnome app like gnome-app-manager or synaptic loads all the gnome libraries as well, so you lose the benefit of the slim desktop. Something like fluxbox with aterm works very well, no matter what the distro on my Pentium 2 with 64 mb ram as long as I don't run any kde or gnome apps.

Sam

---

### Post by RedSquirrel on 2007-10-18
> **disasm said:**
> Just a note, loading a gnome app like gnome-app-manager or synaptic loads all the gnome libraries as well, so you lose the benefit of the slim desktop. Something like fluxbox with aterm works very well, no matter what the distro on my Pentium 2 with 64 mb ram as long as I don't run any kde or gnome apps.

Sam

Synaptic is not a GNOME application. Have a look at its dependencies. It is a great deal slower than using the command line for package management, however. :)

OP: I was just skimming through this thread again. As mentioned by MetalMusicAddict, the rest of your system is fine and with just a little more RAM it would be great. If there was any way you could upgrade the RAM, say, even to 128 MB or 256 MB, Xfce would run quite well. You are, of course, welcome to give a minimal installation a whirl or try a lighter distribution. Good luck. :)

---

### Post by NT4usB on 2007-10-18
I'm not sure just RAM fixes these things...
I put Xubuntu 6.10 on a PIII 550/100 (Intel i810) with 768 MB ram and it was painfully slow. Grow old waiting for a terminal to open.
I ran NT4 then 2K on this box for years and it was fine. Not blazingly fast but usable for sure. Even ran SolidWorks ok.

More recently, I Loaded the same disk on a PIII 733/133 (Asus SIS) with 384 MB and it's fine. Firefox and all the rest are acceptably responsive.
I don't think the 733 is twice the box as the 550, but it runs apps easily four times faster than the 550.

---

### Post by kerry_s on 2007-10-18
> **NT4usB said:**
> I'm not sure just RAM fixes these things...
I put Xubuntu 6.10 on a PIII 550/100 (Intel i810) with 768 MB ram and it was painfully slow. Grow old waiting for a terminal to open.
I ran NT4 then 2K on this box for years and it was fine. Not blazingly fast but usable for sure. Even ran SolidWorks ok.

More recently, I Loaded the same disk on a PIII 733/133 (Asus SIS) with 384 MB and it's fine. Firefox and all the rest are acceptably responsive.
I don't think the 733 is twice the box as the 550, but it runs apps easily four times faster than the 550.


xubuntu is bloated, try debian and you will see the difference, it ran fine on mine with 450mhz 256ram.
[http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-xfce-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-xfce-CD-1.iso)

if you really want speed, go custom install and use faster applications.

---

### Post by z0phi3l on 2007-10-18
> **NT4usB said:**
> I'm not sure just RAM fixes these things...
I put Xubuntu 6.10 on a PIII 550/100 (Intel i810) with 768 MB ram and it was painfully slow. Grow old waiting for a terminal to open.
I ran NT4 then 2K on this box for years and it was fine. Not blazingly fast but usable for sure. Even ran SolidWorks ok.

More recently, I Loaded the same disk on a PIII 733/133 (Asus SIS) with 384 MB and it's fine. Firefox and all the rest are acceptably responsive.
I don't think the 733 is twice the box as the 550, but it runs apps easily four times faster than the 550.

I had Zenwalk running mighty fast on a Celeron 566, 60gb HDD, and little over 300mb RAM

Yes Firefox was slow but then again it was a Celeron :P

---

### Post by dexterbt1 on 2007-10-18
Up until recently, dapper xubuntu ran quite well for about 1 year on my old notebook with the ff. specs:
- celeron 450MHz
- 128MB ram
- 10gb hdd

note that i was even doing development on that stuff months ago. I was running firefox, Terminal (xfce-gtk2-based), vim, gimp, lighttpd, mysqld, xmms, even amarok. 

But multitasking is limited if you don't manage it carefully. I really did pay attention to the memory/swap usage. At boot-up, xubuntu dapper can do 90+mb memory, at least IIRC. 

Don't count office apps though,  OO loads for ages (5-10mins), even gnumeric or abiword would load for like around a minute or so. 

Anyway, again, the key is watching your memory/swap. Turn off unnecessary services. Run the lightweight counterparts of the programs.     

I'm posting this message actually using my own xubuntu feisty notebook; which has a sempron 1.8GHz and a 512ram (128 for vram). My system currently consumes 300mb of 384mb rss and 284mb of 2GB swap, all with around 20 tabs on firefox and multiple tabs on terminal; along with gaim, xmms, mysql, postgres, etc running in background.

Cheers!

---

### Post by TeaSwigger on 2007-10-19
Some stats if they're of interest to anyone.

Memory usage notes. Taken via htop running in urxvt default config. Unit - Dell Dimension 4100 PIII 933mhz 384mb ram 64mb nvidia gfx. No swap in use. Use - at idle, that is ~58 running processes in bg, no apps open. Stat 1 - from fresh boot. Stat 2 - after a few hours operation, after open apps closed.

ubuntu - 108mb / 134mb
kubuntu - 99mb / 138mb
xubuntu - 101mb / 128mb

on kubuntu as WM:
WindowMaker - 77mb / 91mb
IceWM - 74mb / 93mb
Fluxbox - 72mb / 94mb

In actual light use, the "Big Three" seem to hover around ~130 - 180mb while the "Light Three" take ~110 - 170mb, all liking to settle to using roughly ~40mb swap (if using similar apps, icons etc of course). So no surprises, but it bears out the advice that if one wants to use a 256mb unit it's gonna be slow going, and any less should go with a leaner setup than any of the *buntus offer by default.

---

