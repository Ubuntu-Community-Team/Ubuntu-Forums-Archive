---
title: "MapleStory for Linux?? (using wine) HELP!"
date: 2009-07-09
forum: Gaming &amp; Leisure
---

### Post by Ziraider on 2009-07-09
Hello, I currently switched to using Linux Ubuntu not to long ago. Deleting my windows (prolly bad thing to do but w.e) Well, I'm having a little Trouble geting MapleStory to work on wine. Any way you guys can help?

---

### Post by binbash on 2009-07-09
It does not work with wine.MapleStory only works with virtualbox on Linux, for now.

---

### Post by Ziraider on 2009-07-09
Thanks, I will have to download!

---

### Post by BoyOfDestiny on 2009-07-09
I don't have this game, but I thought I would elaborate on the above post. 

The main (only?) reason it doesn't run under wine is due to Maple Story using [gameguard]("http://en.wikipedia.org/wiki/NProtect_GameGuard")

You can see the bug reports for Maple Story on wine here.
[http://bugs.winehq.org/show_bug.cgi?id=3952](http://bugs.winehq.org/show_bug.cgi?id=3952)

Now, as was mentioned, you can use [virtualbox]("http://www.virtualbox.org/"). This is a virtual machine or emulator, that you can install Windows XP (or pretty much any x86 OS), and run any application within it.

A good alternative to dual booting, as there is support for 3D acceleration now.

---

### Post by Ziraider on 2009-07-09
Well, thats diffrent, so in using an antihack program it wouldnt work? or is it just gameguard? because the Switched to Antlab fr antihacks

---

### Post by J03y on 2009-07-09
nvm

---

### Post by Ziraider on 2009-07-09
J03y, i seen what you said >_> about playing private server, and well... i played a few. but then most of the really good ones went down, so i went back to GMS because the fact the KNCS are coming out.

---

### Post by Ziraider on 2009-07-09
Note: Vbox didnt work with maplestory, is there anyother way to get the game to work?

---

### Post by Grishka on 2009-07-09
> **Ziraider said:**
> Note: Vbox didnt work with maplestory, is there anyother way to get the game to work?

No. gameguard does not work with wine. but why didn't it work in virtualbox? did you get the [latest version](http://www.virtualbox.org/wiki/Linux_Downloads)?

---

### Post by aanderse on 2009-07-10
somewhat related, i suppose:
[http://irrlicht.sourceforge.net/phpBB2/viewtopic.php?t=33223](http://irrlicht.sourceforge.net/phpBB2/viewtopic.php?t=33223)

---

### Post by Nevon on 2009-07-10
I thought it only worked in VMware?

---

### Post by jnw222 on 2009-07-10
sun added 3D support in the new 3.0

---

### Post by Nevon on 2009-07-11
> **jnw222 said:**
> sun added 3D support in the new 3.0

Yes, but only for Linux guests, right?

---

### Post by Grishka on 2009-07-11
> **Nevon said:**
> Yes, but only for Linux guests, right?

[no](http://www.virtualbox.org/manual/UserManual.html#guestadd-3d).

---

### Post by Nevon on 2009-07-11
> **Grishka said:**
> [no](http://www.virtualbox.org/manual/UserManual.html#guestadd-3d).

Oh, cool! If I wasn't completely sick of Maplestory, I'd install it in virtualbox.

---

### Post by Ziraider on 2009-07-13
Yeah, I'm Pretty sure that I have the newest Vbox.

Dosnt VmWare cost money?

---

### Post by Grishka on 2009-07-13
> **Ziraider said:**
> Yeah, I'm Pretty sure that I have the newest Vbox.

Dosnt VmWare cost money?

the player is free, but you'll need a Windows image. to make one, you'll need the server software. been a while since I've used vmware, don't remeber well, but I think it was free. or maybe there was a free trial for the server software. just [check it out](http://www.vmware.com/) by yourself, no one will tell you if it works for YOU anyway. but you still didn't say what are your issues with Virtualbox? note that for the 3d acceleration to work, the guest addons have to be installed in safe mode, else windows overwrites the custom drivers.

---

### Post by Ziraider on 2009-07-13
> **Grishka said:**
> the player is free, but you'll need a Windows image. to make one, you'll need the server software. been a while since I've used vmware, don't remeber well, but I think it was free. or maybe there was a free trial for the server software. just [check it out]("http://www.vmware.com/") by yourself, no one will tell you if it works for YOU anyway. but you still didn't say what are your issues with Virtualbox? note that for the 3d acceleration to work, the guest addons have to be installed in safe mode, else windows overwrites the custom drivers.


Well. I'm pretty sure that I installed the program right, but I'm not sure how to use it for the most part I believe, once I open the program I tell Vbox to power up. It starts right up says something bout an autocaputre keyborred, I click okay then I get this Error: FATAL: No bootable medium found! System Halted! 


That my main problem. But yeah, I'm lost.

---

### Post by Grishka on 2009-07-13
> **Ziraider said:**
> Well. I'm pretty sure that I installed the program right, but I'm not sure how to use it for the most part I believe, once I open the program I tell Vbox to power up. It starts right up says something bout an autocaputre keyborred, I click okay then I get this Error: FATAL: No bootable medium found! System Halted! 


That my main problem. But yeah, I'm lost.

do you have the Windows installation disk? press ctrl+d in virtualbox and create a new virtual disk. give it a few gigabytes of space. mount it from the settings and mount the Windows install dvd as well. run your virtualbox session, boot it from the windows install dvd, and install Windows like you normally would.

---

