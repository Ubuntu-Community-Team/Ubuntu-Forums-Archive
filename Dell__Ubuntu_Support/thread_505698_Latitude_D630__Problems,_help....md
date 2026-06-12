---
title: "Latitude D630 | Problems, help..."
date: 2007-07-20
forum: Dell  Ubuntu Support
---

### Post by alecwh on 2007-07-20
Hey!

I know there is a master topic for this PC, but I posted and didn't seem to get an answer. I have a WiFi card (see below), and cannot seem to get it working.

I did this:

```

alec@aleclaptop:~$ sudo modprobe ipw3945
2007-07-19 22:01:57: ERROR: Could not find Intel PRO/Wireless 3945ABG Network Connection

```

How do you do fix this? I really really really need wifi, I'm sick of being confined with an ethernet cable.

My next problem, is Compiz-fusion. I installed it, and ran it, but it just freezes my system. I have pretty good specs, Intel core 2 duo, 1gig ram.... it should work flawlessly, especially on a dell system. I don't know what's wrong.

I also feel as if the colors are set to "256" or something (like windows) because gradients are all blockish... It's a weird problem.

Can someone help me out here?

---

### Post by angryfirelord on 2007-07-31
Are you positive that it's a 3945 chipset? Mine works perfectly under Ubuntu.

Post the output of **lspci**.

---

### Post by purplearcanist on 2007-07-31
> **alecwh said:**
> 
My next problem, is Compiz-fusion. I installed it, and ran it, but it just freezes my system. I have pretty good specs, Intel core 2 duo, 1gig ram.... it should work flawlessly, especially on a dell system. I don't know what's wrong.


What is your graphics card?
If it is a 	
Intel®  Graphics Media Accelerator X3100, then upgrading to Gusty Gibbon will solve this problem, as the driver for this graphics card is bad in Feisty, but good in Gusty.

---

### Post by rmullins on 2007-07-31
how stable is gutsy.  I know its beta but is it stable.

I installed on my intel 3100 with feisty but the graphics suck big time,   I don't drivers for cd/dvd burner are gone too.  Plus it was a work-around to get it up and running, which I don't fully trust as a production box.

---

### Post by rmullins on 2007-08-01
Ok, just tried to install gutsy.  It's pretty much a crap install as well as feisty, and edgy when trying to install on newer hardware.

I currently have a new Latitude D830 with the Intel 3100 graphics card.  EVERY ubuntu ISO dumps me in busy box as it tries to load the drivers for the graphics card when simply booting up the disk.

I know there is a work around, but that isnt the point.  The disk should be plug and play enabled.  Put it in and go through a doze install.

Gutsy might have the right drivers, but Im not going to go through the trouble of burning DVD disk, installing in text mode, blah, blah, blah.

Either Ubuntu or Intel need to fix it.  Not provide another thing to go to, just fix it.  This is really getting old.



(Incidentally this is not my first cup of ubuntu.  I have had to recreate my account due to some strange stuff with the way the forums were handling my information.)

---

### Post by angryfirelord on 2007-08-01
> **rmullins said:**
> Ok, just tried to install gutsy.  It's pretty much a crap install as well as feisty, and edgy when trying to install on newer hardware.

I currently have a new Latitude D830 with the Intel 3100 graphics card.  EVERY ubuntu ISO dumps me in busy box as it tries to load the drivers for the graphics card when simply booting up the disk.

I know there is a work around, but that isnt the point.  The disk should be plug and play enabled.  Put it in and go through a doze install.

Gutsy might have the right drivers, but Im not going to go through the trouble of burning DVD disk, installing in text mode, blah, blah, blah.

Either Ubuntu or Intel need to fix it.  Not provide another thing to go to, just fix it.  This is really getting old.



(Incidentally this is not my first cup of ubuntu.  I have had to recreate my account due to some strange stuff with the way the forums were handling my information.)
If you used the Live CD, try the alternate cd. Just be patient and you'll solve it.

Also, how did you install the intel driver?

---

