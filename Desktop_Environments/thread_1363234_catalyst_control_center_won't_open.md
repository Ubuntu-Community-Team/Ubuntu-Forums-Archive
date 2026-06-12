---
title: "catalyst control center won't open"
date: 2009-12-24
forum: Desktop Environments
---

### Post by charonred on 2009-12-24
I'm running  Hardy 8.04 and finally upgraded my ATI graphics card from a ASUS EAH3450 to a new Sapphire HD5770.

I downloaded and installed new driver *ati-driver-installer-9-12-x86.x86_64.run* - it seems to be working ok, but I just can't get Catalyst Control Center to run.

I click the link in System > Preferences > ATI Catalyst Control Center and nothing happens; I do likewise with Catalyst Control Center (Administrative) and it prompts for the password, but after entering it, nothing happens.

I have 2 identical Samsung SyncMaster 943N monitors displaying the same 1280 x 1024 desktop; previously I had it running as One Big Desktop (2560 x 1024); but not being able to use CCC, I can't set it top run that way.

Any ideas on how to get CCC working?

---

### Post by kellemes on 2009-12-24
Have you tried it from the commandline? Possibly you'll get some informative feedback.
 Use your menueditor to find the exact command you need to start it from CLI.
If needed, use "gksudo"  for root-privileges..

```
gksudo <ATI-controlcenter command>
```

---

### Post by charonred on 2009-12-24
yep, tried it from Terminal, both as  user & root

```
~$ amdcccle
amdcccle: symbol lookup error: amdcccle: undefined symbol: _Z13qFlagLocationPKc

``` - nothing happens

```
~$ amdxdg-su -c amdcccle

``` - prompts for password, but still nothing happens

I've uninstalled both fglrx-control & fglrx-amdcccle, then reinstalled again via fglrx-amdcccle_8.681-0ubuntu1_i386.deb

Don't know if this has anything to do with it, but I'm still using 2.6.24-23 generic kernel - 2.6.24-24 gave splash screen problems, so I stayed with 24-23, but 24-25 & 24-26 are available as well (I use StartUp-Manager to control which kernel loads)

update: just re-read install guide and kernel shouldn't be a problem;
> Minimum System Requirements
Before attempting to install the ATI Proprietary Linux driver, the following software
must be installed:
 XOrg 6.8, 6.9, 7.0, 7.1, 7.2, 7.3 or 7.4
 Linux kernel 2.6 or above
 glibc version 2.2 or 2.3
 POSIX Shared Memory (/dev/shm) support is required for 3D applications

---

### Post by charonred on 2009-12-24
thought I'd try the earlier version drivers
 *ati-driver-installer-9-11-x86.x86_64.run* which also has support for the 5700 series graphics cards

so I enter 
```
:~/Desktop$ sudo sh ati-driver-installer-9-11-x86.x86_64.run --buildpkg Ubuntu/hardy
```

Same result as the latest version, everytime I try to run the installer I get the following
```
Generating package: Ubuntu/hardy
Resolving build dependencies...
Unable to resolve  can't parse dependency ooobasis31-en_us
 can't parse dependency ooobasis31-en_us-res
 can't parse dependency ooobasis30-en_us-res
 can't parse dependency ooobasis31-en_us-base
 can't parse dependency ooobasis30-en_us-help
 can't parse dependency ooobasis31-en_us-binfilter
 can't parse dependency ooobasis30-en_us
 can't parse dependency ooobasis31-en_us-math
 can't parse dependency ooobasis30-en_us-base
 can't parse dependency ooobasis31-en_us-draw
 can't parse dependency ooobasis30-en_us-binfilter
 can't parse dependency ooobasis30-en_us-math
 can't parse dependency ooobasis31-en_us-impress
 can't parse dependency ooobasis30-en_us-calc
 can't parse dependency ooobasis31-en_us-calc
 can't parse dependency ooobasis31-en_us-writer
 can't parse dependency ooobasis31-en_us-help
 can't parse dependency ooobasis30-en_us-impress
 can't parse dependency ooobasis30-en_us-draw
 can't parse dependency ooobasis30-en_us-writer.  Please manually install and try again.

```
except the latest version actually leaves .deb installers on the desktop which I can sequentially install, the earlier version doesn't leave anything to install.

In either case, in Terminal I'm told to manually install and try again ... install what ...  the ATI package, or Open Office  (and what has that to do with ATI drivers?) - This is frustrating as hell ...

... and while I was typing this, terminal suddenly decided it could parse dependencies and left .deb installers on desktop for earlier version ??? I'l try installing them now.

---

### Post by charonred on 2009-12-24
what a piece of  ****; another day and a half of my life wasted trying to get graphics to work - no way to spend Christmas day, but my PC needs to function properly, or it's no good to me.

The one area where Linux/Ubuntu falls over badly is with graphics card drivers; a simple thing like installing a new card results in hours, if not days of anguish and frustration; with Windows or Mac, just install it and update the drivers... easy! ... makes me re-consider going back to Windows (shudder), but if I can't get graphics working correctly, then what good is a free OS and all the associated PC hardware ?

Can anyone offer advise on how to get a HD5770 card working in Hardy 8.04.3  ?

---

### Post by justman on 2009-12-24
this also happens to me on my ubuntu intrepid. It seems like that the amdcccle of version 9.12 needs the newest libqt (libqt4.5). 

but you can extract amdcccle from another old version fglrx .

```
sh ./******.9.8.*****.run     --buildpkg Ubuntu/hardy
```
then you can find amdcccle deb package, and just install the amdcccle package. It also works fine with driver fglrx 9.12.

---

### Post by charonred on 2009-12-24
thanks justman, 
I had a feeling that the admcccle was at fault ... and of course libqt4.5 isn't available for Hardy 8.04

So if I install everything from 9.12 except for amdcccle, and then install amdcccle from 9.8, then it should work; I'll try that after a cup of coffee (I need a brainbooster)

---

### Post by charonred on 2009-12-24
OK, I now have 9.12 drivers with 9.8 amdcccle (though I have to use Terminal to access it, but that's fine)

I now also have 'single display (multiple desktop)' over 2 monitors; but what I want is 'one big desktop' spread over 2 monitors (like it was with EAH3450 card), but can't see the option for that.

I also want to be able to drag windows from one monitor to the other - also move one panel to the other monitor (I've done this before, but can't remember how)

---

### Post by charonred on 2009-12-25
problem is partway solved; amdcccle now displays and allows setting changes; but I now have 2 desktops, each controlled separately.

I can have Thunderbird open on monitor 1 and Firefox open on monitor 2 (like I used to); but if I click a link in an email on mon#1, it wants to open Firefox on mon#1, but it can't because Firefox is already 'running' on mon#2 and it says I need to close the running Firefox first (before opening it on mon#1), yet I can open another instance of Firefox on mon#2, but not one displaying the page from the email link on mon#1.

What I had before was one big desktop spread over 2 monitors with wallpaper of 2560 x 1024 covering both monitors (I now have identical wallpaper of 1280 x 1024 on both monitors); I could have Firefox open on one, and Thunderbird open on the other, I could drag any application window from from one monitor to the other, I could also re-arrange the panels between monitors. With desktop cube enabled I could rotate both monitors as one big cube, now each monitor has to be rotated separately.

The whole reason I got a more powerful graphics card was to deal with the 'big desktop' resolution of 2560 x 1024 - the EAH3450 would 'bog down' regularly and the screen would 'grey out', despite having a 3.0Ghz Phenom II 945 quad-core CPU & 4GB of DDR2 RAM running @ 1066 Mhz.

Enabling xinerama in amdcccle is of no use because compositing isn't supported and therefore desktop effects can't be enabled.

Any ideas on how to get it working the way I had it before :confused:

---

### Post by charonred on 2009-12-25
Another problem; every 20 minutes or so, both screens slowly fade to grey and then black out completely like it's going into screensaver mode, but then it clears up to normal; this happens even while I'm active on PC. Also, there's a lag in menu items displaying as I click Applications, Places or System and mouse over items (there was virtually no lag with previous card).

It seems there's a conflict between the newest drivers and the Hardy OS; I'm now beginning to question the value of higher end graphics cards given the apparent state of driver support for earlier releases of the OS.

---

### Post by charonred on 2009-12-25
Just to test the card, drivers and OS conflict theory, I did a clean install of Karmic 9.10 on another drive. I let it do the post install updates, then downloaded & enabled the restrictive ATI drivers. 

I set it up as 'multiple desktops (1 display)' which seems to be what was previously named 'One Big Desktop'. It seems to work fine, I have one 2560 x 1024 wallpaper spanning both monitors, and can drag any window from one monitor to the other, and clicking on my email links work as they did before in Firefox; and there's no 'greying or blacking out' of the screen every 20 minutes or so ... brilliant !

So the problem appears to be with the latest drivers (which are needed to support the new card) and Hardy 8.04; I'll keep persevering with Hardy for a while and see if I can get it to behave, if not I may have to migrate to Karmic 9.10.

As my PC is primarily for business, I was planning on leaving my next OS migration until Lucid Lynx 10.04 LTS was released; but having 1 big desktop spread over 2 monitors (which makes work so much more efficient), may just force an intermediate migration to Karmic.

---

### Post by charonred on 2009-12-28
I don't know exactly how, but since all this fiddling to get the HD5770 drivers to work in Hardy, it seems to have 'broken' the Hardy install;
[LIST]
[*]The system sometimes hangs partway through it's shut-down - after 10 minutes there's still just a black screen with text on it, and I have to switch the power off.
[*]the previously mentioned 'greying' then 'blacking' out of both screens as if it's going into screensaver mode when I'm working in an application - frustrating cause I can't do anything till the screen normalises.
[*]occasional total freeze of mouse and keyboard, requiring a hard reset
[*]increased 'lag' times in displaying menu items, and also applications 'lag when opening.
[/LIST]
So it appears that the ATI 9.12 drivers combined with 9.8 Catalyst Control Centre don't actually work together that well in Hardy, to the extent that somehow they've messed the system up.

I have none of these problems if I boot to Karmic, so the migration is looking immanent.

---

### Post by charonred on 2010-01-03
Well, I've spent the last few days migrating my system settings/customisations, email and accounts/passwords, and other applications across to Karmic. I've undoubtably missed something, but will sort that out as they become apparent. 

Otherwise Karmic 9.10 is running fine, as its the HD5770 card, ATI drivers and CCC - both monitors are happily running as one big desktop, so I'm pretty happy with the setup now.

---

### Post by RMcD94 on 2011-02-17
I have the same problem as the original post, however ATI Catalyst Control Center opens, but ATI Catalyst Control Center (Administrative) does not (no option for password entering or anything), which means I cannot change the display settings, and I don't want both displays to be a clone. 

How do I solve this? I read the thread; I have no idea what anyone's talking about.

---

### Post by deeaycee on 2011-02-22
> **RMcD94 said:**
> I have the same problem as the original post, however ATI Catalyst Control Center opens, but ATI Catalyst Control Center (Administrative) does not (no option for password entering or anything), which means I cannot change the display settings, and I don't want both displays to be a clone. 

How do I solve this? I read the thread; I have no idea what anyone's talking about.

I have the same problem as you but as a temp work-around
you can get the ATI admin app to open by opening a terminal session and typing in "amdxdg-su -c amdcccle" without quotes.
a window should pop up asking for your admin password. once that's accepted, the ATI Catalyst Control Center opens and you can make your changes.

---

### Post by ackmanx on 2011-05-23
> **RMcD94 said:**
> I have the same problem as the original post, however ATI Catalyst Control Center opens, but ATI Catalyst Control Center (Administrative) does not (no option for password entering or anything), which means I cannot change the display settings, and I don't want both displays to be a clone. 

How do I solve this? I read the thread; I have no idea what anyone's talking about.

Another solution... In terminal I just did "gksudo amdcccle" and successfully was allowed as admin. I'm using Xubuntu 11.04, so maybe it doesn't apply to you but worked for me.

---

