---
title: "Installed 8.10 from flashdrive with wubi on XP PC"
date: 2009-01-03
forum: General Help
---

### Post by cybrsaylr on 2009-01-03
Did the install on my sister's Compaq, 3.0Mhx celeron with 512RAM, 100GB HDD.
The install went OK except for stalling once. Restarted and it completed the wubi install. XP boots OK and so did Ubuntu on first bootups. 

Played around with 8.10 a little and it seemed slower than my 2 PCs that have 8.10 installed as a dual boot with XP and Vista. Firefox took awhile to load then ran slow at first but seemed to pick up speed after a little use. Couldn't get Rhythmbox to open or play at all....it kept timing out. Checked out 'system monitor', it took a long time to load up and memory use was over 300Mb at idle! CPU was nice and low though <14%. 

Had to leave my sister and set up the updates to DL and install the 207 updates to bring 8.10 up to date. It started out OK then froze midway through. My sister told me this when I got home. She knows nothing about Ubuntu and did a hard 'forced shutdown' and went back to XP. 

Only played around a little after the 8.10 install and noted everything loads slow. Terminal also took too long to load up and show its screen. Same with screen resolution when I opened it to change screen resolution and the refresh rate to a better setting. 

Is this normal? Would I be better off installing 8.10 as a dual boot instead of with wubi inside of Windows? At first I wanted to do a dual boot setup but her PC would not boot up off the USB flashdrive......I tried a few things but it would not bootup. At that point I wished I had brought the 8.10 install CD along instead of the flashdrive! So then I installed with wubi that went OK except for that one time it stalled out and had to be restarted.

The question is, should I reinstall as a 'dual boot' or is there a way to speed things up in wubi? Does running 8.10 inside Windows slow 8.10 down like it is?

---

### Post by creek23 on 2009-01-03
> **cybrsaylr said:**
> [COLOR="Red"]3.0Mhx[/COLOR] celeron with 512RAM

I hope that you have 3.0GHz typo. A 3.0MHz is way too slow. ;)

Okay, for your questions:

**Would I be better off installing 8.10 as a dual boot instead of with wubi inside of Windows?** Basically, WUBI slow but not to the point that it freezes your PC. If that's the case, then try to defrag Windows (with Defraggler).

The only reason WUBI is a "little" slower than native install is that the file **root.disk** under **C:\ubuntu\disks\** of Windows is being read-from and written-to by Ubuntu. That **root.disk** is around 4GB (depending on your setup configuration). You'll understand just how slow that can be when you try to open root.disk with Windows' Notepad.

With just 512MB of memory, you PC struggles so hard to open such huge file. I suggest that you upgrade to at least 1GB (I suggest 2GB, anyway).

**should I reinstall as a 'dual boot' or is there a way to speed things up in wubi?** Are you ready to convert yourself as GNU/Linux user? WUBI's main concern is for you to try out Ubuntu; installing it natively means you want to use it for a while or, probably, longer.

**Does running 8.10 inside Windows slow 8.10 down like it is?**

Not in my 1GB laptop. And oh, Ubuntu boots up without the need of Windows -- it just needs the *root.disk* file from that partition.

---

### Post by cybrsaylr on 2009-01-03
creek23,
Thanks for the answers.

Yes it was a typo, it's a 3.0Ghz PC.

My sister did defrag before 8.10 was installed. She had some spyware issues in XP that I cleaned out. I suggested she try Ubuntu to escape these spyware/malware/AV issues. 

This is my first experience using 'wubi'. Been using Ubuntu for 2 years in a couple dual boot systems which both performed faster than what I saw on her PC with a wubi install of 8.10. 

I realize 512MB RAM is low but I have a 12yr old Pent2 400Ghz PC with 384MB RAM that runs both XP and 8.10 and 8.10 runs better on my old P2 than her 4yr old 3.0Ghz Celeron. I suspected running 8.10 though in Windows the way you explained with only 512MB RAM would slow things down.

My newer laptop an AMD 2.0Ghz dual core with 4GB of RAM runing a dual boot of Vista/Ubuntu 8.10 really flies. In fact 8.10 runs faster than Vista.

If she likes Ubuntu I will probably delete the wubi install and put 8.10 in as a dual boot setup like in my other two PCs. 

If I decide this, what's the best way to remove wubi 8.10?
Just delete that 15GB Ubuntu 8.10 folder in Windows or do the uninstall that is found in the Ubuntu 8.10 folders?

---

### Post by creek23 on 2009-01-07
> **cybrsaylr said:**
> creek23,
Yes it was a typo, it's a **3.0Ghz** PC.

...

I realize 512MB RAM is low but I have a 12yr old Pent2 **400Ghz** PC with 384MB RAM

There you go again. :P

> **cybrsaylr said:**
> In fact 8.10 runs faster than Vista.

To be fair with Vista, one reason it runs slow at boot and upon login is that it tries to check the registry and sytemfiles for their integrity -- you end up waiting for it to finish. :(

> **cybrsaylr said:**
> what's the best way to remove wubi 8.10?
Just delete that 15GB Ubuntu 8.10 folder in Windows What the? You really had to use 15GB for Wubi? If you want her to try it and have fun with it, use a minimum of 4GB. If you are to install any games like UrbanTerror, PlaneShift, etc, install it in **/host/ubuntu/{here}**.

This way, Wubi will only have to read 4GB of chunk and boot lightning fast. ;)

> **cybrsaylr said:**
> or do the uninstall that is found in the Ubuntu 8.10 folders?

Use **uninstall** instead -- it will change back the MBR.

---

