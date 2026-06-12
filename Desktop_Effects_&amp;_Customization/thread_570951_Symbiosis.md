---
title: "Symbiosis"
date: 2007-10-08
forum: Desktop Effects &amp; Customization
---

### Post by Officer Dibble on 2007-10-08
There appears to be a graphical symbiosis between my dual boot of XP and Ubuntu...:-k

I was updating my Nvidia drivers for XP, and on completion Windows wanted to restart and did so. It just so happens that during the restart I selected to go into Ubuntu by accident. (out of habit) Something strange happened, the resolution had mysteriously changed to something like 640x480 and wouldn't change - I was confused because I hadn't changed anything in Ubuntu.

So, I restarted the computer and this time booted into XP as I originally intended. Everything was fine, the drivers had installed just fine. Once happy with that I then restart my computer with the purpose of sorting out the problem with Ubuntu, my favorite OS.

Guess what I found? There was nothing wrong with it... it had been corrected... now my question is this, does Ubuntu in anyway depend or in some ongoing manner use the driver configuration of Windows?

Thank you. :)

---

### Post by 1337455 10534 on 2007-10-08
It cant, its on a different partition... People may say there is no such thing as coincidence, but I think somewhere Ubuntu just goofed (as stable it may be..)

---

### Post by Officer Dibble on 2007-10-09
> **1337455 10534 said:**
> It cant, its on a different partition... People may say there is no such thing as coincidence, but I think somewhere Ubuntu just goofed (as stable it may be..)

Exactly what I thought... is it possible that Ubuntu 7.04 was "borrowing" Nvidia drivers from my XP install?

---

### Post by jespdj on 2007-10-09
> **Officer Dibble said:**
> Exactly what I thought... is it possible that Ubuntu 7.04 was "borrowing" Nvidia drivers from my XP install?
No, that's not possible. Ubuntu does not use Windows drivers, and it certainly does not look at your Windows partition to find drivers.

It must have been a coincidence. Maybe the last time you used Ubuntu an update was downloaded which got activated now?

---

### Post by Officer Dibble on 2007-10-09
> **jespdj said:**
> No, that's not possible. Ubuntu does not use Windows drivers, and it certainly does not look at your Windows partition to find drivers.

It must have been a coincidence. Maybe the last time you used Ubuntu an update was downloaded which got activated now?

This is my story...

I was using Ubuntu 7.04, downloading a theme for my phone. Bluetooth still doesn't work on Ubuntu so when the download has finished I emailed the theme to myself so that I can pick the file up by checking my mail in XP and transfer it from there... so the download finishes and I restart my computer to get into XP.

On starting XP I started looking for my bluetooth icon on my desktop (which is littered with shortcuts :oops:) and in frustration decide to start dropping anything and everything into a separate folder on my desktop... when suddenly I find my Steam shortcut... not played CS in a while you see... so I run it and I am told that my Nvidia video driver is out of date, and being the obedient chap I am I download and install them.

Once installed Windows wants the computer to restart... so being the obedient chap I am, yes you get the idea... During restart I accidently allow the computer to boot into Ubuntu rather than select XP in the Grub menu. (dual booting) I let it finish booting into Ubuntu and Lo and Behold... my resolution had changed to something like 640x480 and it won't let me change it to anything else!! Compizz and Beryl still work perfectly, but I am in a really low res, which is a bit naff and made me rather niggled...

After having looked around for means and ways to correct the problem I wondered if the problem was in some way connected to the fact I had just updated the Nvidia drivers for XP... I thought to myself that this couldn't be possible as both OS's have a different architecture, etc. But I restarted all the same to test the theory, this time allowing the computer to restart into XP.

XP boots up, or rather cranks itself up and the driver update had gone through fine. Windows looked normal. I went ahead and did the bluetooth transfer and then decided to have another look at my new issue with Ubuntu, restarting the computer.

The computer restarts and I log in, and guess what? Ubuntu looks just fine and dandy. At this point all I could relate it to was the change in video drivers in XP... dunno what to say beyond this really. :)

---

### Post by 1337455 10534 on 2007-10-10
Perhaps try Administration-->Services and enable all Bluetooth options??

---

