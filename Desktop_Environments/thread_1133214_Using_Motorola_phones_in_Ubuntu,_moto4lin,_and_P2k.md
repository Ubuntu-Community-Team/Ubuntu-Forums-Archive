---
title: "Using Motorola phones in Ubuntu, moto4lin, and P2k Commander"
date: 2009-04-22
forum: Desktop Environments
---

### Post by fondfire on 2009-04-22
I have a Motorola RAZR V3xx, and naturally, I wanted a Linux application to upload and download files to it.  I immediately found moto4lin in the repositories and was really pleased, downloaded it . . . and proceded to have perhaps my worst Ubuntu experience ever, as [my model is simply not supported in moto4lin]("http://moto4lin.sourceforge.net/wiki/Razr_V3xx").

Well, after some digging, I found a great new solution called [P2k Commander]("http://www.el-co.hu/smf/").  It looked great and promised to work for a RAZR V3xx.  And it did!  I'm quite pleased.

However, it was tricky to get it installed.  To make it easier on everyone else, I compiled a debian package, which I'm providing here: [http://sites.google.com/site/fondfire/ubuntu/pool/universe/p/p2kc/p2kc_0.6-0ubuntu1_i386.deb]("http://sites.google.com/site/fondfire/ubuntu/pool/universe/p/p2kc/p2kc_0.6-0ubuntu1_i386.deb").  Maybe some nice Ubuntu developer can pick-up [the sources I used]("http://sites.google.com/site/fondfire/ubuntu/pool/universe/p/p2kc/") and plug it into the official universe repositories.  (BTW, if you're using the AMD64 build, you'll want [this package]("").  If you're not sure, stick to the i386 package linked above, as that's almost surely what you neeed.)

I hope some of you find P2k Commander useful.  Oh, and once you download the package, install it like so:

[INDENT]```
sudo dpkg -i p2kc_0.6-0ubuntu1_i386.deb
```[/INDENT]

Hope this helps out somebody else here!  It would be nice to think this package helps.  Thank s5vi if it actually works, though!  :D

--Fondfire

---

### Post by albertu on 2009-04-27
How can I install some skins with this application ?
I have v3xx,too
thx
:(

---

### Post by ceciliaFX on 2009-05-10
thank you for this link!
a friend has an old Moto razr phone and wanted to get the photo's off of it. I figured i'd try this.
downloaded the program, ubuntu automatically installed it and I used it.

one thing I found was that the program closes ("crashes"?) when I tried to create a directory on my hard drive.
not a big deal, really. I just created the directory from the OS, then used P2K to copy the images over. easy to figure out.

thanks again

---

### Post by robie69 on 2009-05-15
I'm having the same crashing problem with p2kc. Unfortunately I'm not versed enough in Terminal to be able to mount the device myself. any chance you could show me what to to, or point me to a forum that will, or Flame me for being a noob? Eaither way, I'll learn something.
-robie

---

### Post by ceciliaFX on 2009-05-16
> **robie69 said:**
> I'm having the same crashing problem with p2kc. Unfortunately I'm not versed enough in Terminal to be able to mount the device myself. any chance you could show me what to to, or point me to a forum that will, or Flame me for being a noob? Eaither way, I'll learn something.
-robie

if you mean you don't see your phone showing up when you plug it in, just boot your Ubuntu with the phone ALREADY plugged in - it should be seen automatically. At least that's what happened with me.

I have yet to type anything in a terminal - I HATE typing and don't want to mess things up. So, I try to do things the easy way  :D

---

### Post by fondfire on 2009-08-16
Glad to see there's been some interest!  Sorry I haven't replied before.  I've been quite busy . . .

First off, there's a big problem with how p2kc handles filenames (or directory names) with spaces in them.  It just totally chokes on any spaces, which is absurd.  I'll be asking [s5vi]("http://www.el-co.hu/smf/") about that and maybe he can release a v0.7 with this fixed . . .

@albertu -- Installing skins and themes isn't too hard, but you will need to poke around a bit and think about it, I'm afraid.  There should be a folder named '/e/mobile/skins' on your phone.  Create a new subdir for the new Skin/Theme, place all the *.ski and *.dat files into that new subfolder, and then place any *.jpg files into the '/e/mobile/picture' folder.  I *think* that will install a skin.  If the program gives you any trouble, you can try using the 'sudo p2k-core' program, but it's much harder that way.

@ceciliaFX -- I'm glad it came in handy for you!  And thanks for helping others.

@robie69 -- you're probably experiencing the problem with spaces.  I'll post something if s5vi fixes that . . .

Thanks, all!

--fondfire

---

### Post by tehGriggs on 2009-10-22
Really good package Fondfire. It works great, other than that previously mentioned crashing ;) . Unfortunately for me, I can't seem to get p2kcommander to locate a specific "motorola" folder on my Krzr. Whenever I plug in the phone, it displays a message that some folders are still hidden. I can see a bunch of other folders and files, just not the one I need :S

I'm pretty much using p2kcommander "out of the box" and am fairly new when it comes to messing around with cell phones, so I was just wondering if anyone has any idea how to get that "secret" folder to show up :D

Thanks :D

---

### Post by ceciliaFX on 2009-10-23
> **tehGriggs said:**
> Really good package Fondfire. It works great, other than that previously mentioned crashing ;) . Unfortunately for me, I can't seem to get p2kcommander to locate a specific "motorola" folder on my Krzr. Whenever I plug in the phone, it displays a message that some folders are still hidden. I can see a bunch of other folders and files, just not the one I need :S

I'm pretty much using p2kcommander "out of the box" and am fairly new when it comes to messing around with cell phones, so I was just wondering if anyone has any idea how to get that "secret" folder to show up :D

Thanks :D

my friend's phone files show up under "c:"
I can choose between p2k:/a, p2k:/b, p2k:/c: and p2k:/e
but for me only "c" accesses the phone files.

---

### Post by tehGriggs on 2009-10-23
Hmmm... when I run p2kcommander I detect files on both "a" and "b" but neither locations have the folder i'm looking for. If i select "c", it either crashes or says 0 files found. I notice in p2kcommander's preferences that there is "mode a" set by default... does anyone know what that means and/or if there are any other modes to chose from ?

---

### Post by werny on 2009-11-09
I have installed p2k commander, plugged my phone in via usb, motorokrz6m, but p2kcommander refuses to find the phone, any suggestions?

---

### Post by werny on 2009-11-13
> **werny said:**
> I have installed p2k commander, plugged my phone in via usb, motorokrz6m, but p2kcommander refuses to find the phone, any suggestions?
anyone have any help for me?

---

