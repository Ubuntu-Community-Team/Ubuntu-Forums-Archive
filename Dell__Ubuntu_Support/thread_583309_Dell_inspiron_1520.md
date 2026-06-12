---
title: "Dell inspiron 1520"
date: 2007-10-20
forum: Dell  Ubuntu Support
---

### Post by qbox on 2007-10-20
Hi. I have dell inspiron 1520. The configuration is:

Intel core 2 duo T7300
2gb ram dual channel DDR2
intel graphic media accelerator X3100
integrated 10/100 Network card and modem
CD/DVD RW
Dell Wireless 1505 Wireless-N Mini-card

When I install ubuntu 7.10:

sound card doesnt work
extra buttons on the front side doesnt work
wireless card doesnt work
beryl work for once and afred that ...pff

I spend 2 days for googling and find some solutions but I steel have problems

I install alsa sound card drivers and remove it so I got a sound but the sound is low.
extra buttons is working only visually. when I pussh button I see grafick to set up suond but the volume is the same
I cant faind drivers for wireless card and I can install it
beryl start only once and after that I cant install it again

I need help. Thank you.

---

### Post by Dellfan on 2007-10-20
Weird.... I have a 1505 with nvidia, intel 3945, and T5300 works with Gutsy. Sound worked out of the gate, suspend/resume works after a bit of tweaking. The front buttons worked without any changes (both the volume, and the player buttons in various media players).

Probably have to wrap the Window's drivers for the 1505 using ndiswrapper.

Was your install a clean install or an upgrade?

---

### Post by linux23dragon on 2007-10-20
Hi qbox

Everyone with the Inspiron is having the same sound card issues with Gusty.

Have a look at this [[COLOR="Blue"]*thread*[/COLOR]]("http://ubuntuforums.org/showthread.php?t=530374&highlight=dell+1520")

---

### Post by qbox on 2007-10-20
linux23dragon iv got a sound. but its too.. low

---

### Post by shkbobo on 2007-10-20
> **qbox said:**
> linux23dragon iv got a sound. but its too.. low

I had the same problem.

Fixed it by installing linux-backports-modules-generic but the volume was too low.

I went into the Volume Control and added "Front" in the Edit->Preferences.  Put that up and it was a lot better.

I would check all of the them just to see if there's anything else that may be muted or lowered.

---

### Post by qbox on 2007-10-20
> **shkbobo said:**
> I had the same problem.

Fixed it by installing linux-backports-modules-generic but the volume was too low.

I went into the Volume Control and added "Front" in the Edit->Preferences.  Put that up and it was a lot better.

I would check all of the them just to see if there's anything else that may be muted or lowered.

Thank you shkbobo that was helpful.
sound is ok. Some solution for front side buttons and wireles card?

Thank you

---

### Post by pacut on 2007-10-25
Gentlemen,

does internal modem of 1520 work under Ubuntu ? I am not particularly interested on 7.10, even earlier versions would be ok.

Before buying 1520 latest version (colored !) I need to know if I can have my dial up working.

Thanks !
paolo

---

### Post by qbox on 2007-10-29
Sorry sir. I don't know but you can make a new post under Networking & Wireless forum.

---

### Post by celavek on 2007-12-31
I have some issues with 1520 and Gutsy.
The main issue is that i cannot log out.
When i try to log out instead of the login prompt my screen just freezes. Nothing works anymore and i have to restart my machine. Also if i switch users and i try to turn off the machine from one of the users i get to the same result.
In both situations I cannot even get to the text console, it's just unusable - everything stops responding.

---

### Post by SLA_leandrin on 2007-12-31
dbox

Have you installed Ubuntu 7.10 from the DVD ISO provided by DELL or just with a regular CD??

The link for the DVD ISO for the Inspiron 1520 is [this]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10#Dell_OS_Reinstallation_7.10_DVD_ISO").

---

### Post by celavek on 2008-01-01
No, i haven't used the Dell image. I used the one from the ubuntu sit. Does it matter? I have not seen the issue i mentioned in the FAQ on the page you provided the link for.

---

### Post by meateater on 2008-01-02
The dell ubuntu page has the image for the 1420 inspiron not the 1520. Will the 1420 image work for the 1520? 

Or is it fine to use the 1420 image on the 1520?

---

### Post by kryth on 2008-01-02
Give it a try and let's us know! :D

---

### Post by azjimmy on 2008-01-04
Ive got a 1520 and just used the Dell restore disk and it enabled just about everything right off the bat. 

My configuration

Dual Core T7500
NVidia 8600GT
Intel 3945 ABG WLAN
Conextant Modem

The laptop came installed with XP, but I thought I would try Ubuntu. The DVD installed and enable the restricted drivers for the video card, the wireless, and modem. I followed the instructions provided on the DVD  download page, not the "live" portion.
I haven't updated yet or tried and eye candy like Compiz. I'll post back with more results
Jim

---

### Post by me.translucent on 2008-04-19
thanx dude that front thing worked for me too .. though i have no idea what it is :P

---

