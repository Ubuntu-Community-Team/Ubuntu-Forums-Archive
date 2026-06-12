---
title: "Removed cdrom drive now not boot"
date: 2009-04-14
forum: General Help
---

### Post by s4mur41j4ck on 2009-04-14
ok so i dont know whats going on here
1st let me say i have a 
via EPIA 5000
533MHz samuel 2 core

i managed to get ubuntu 7.10 installed, i updated as much as i can, without going to 8.04.
with install/updates finished i figure i can disconnect the cdrom drive, wrong. the box gets to starting os then instantly shuts off. i would think i was shorting out since it wont turn back on without the power disconnect/reconnect. 

is there something i can disable? because it seems to want the drive connected while booting up the OS. thanks in advance for any help

---

### Post by s.fox on 2009-04-14
Hi,

What happens if you reconnect the cd rom drive?  Does it boot up fine?  I was thinking it might not be the cd rom drive causing the error,  but instead one of the updates.  Easiest was to check would be to reconnect the cd rom drive.

Please post back.

-Ash R

---

### Post by s4mur41j4ck on 2009-04-14
it works fine with the cdrom connected, but this would mean i need a new case for the system in order to keep the cdrom connected. i was hoping to avoid that, plus dont really want an ide cdrom connected

---

### Post by mc4man on 2009-04-14
You could try booting into your bios setup and there should be a place to turn off/remove the cdrom drive (generally in one of the secondary ide listings
(usually pressing F2 or F3 while booting will enter the setup

Just make sure you don't turn off your hdd(s)

---

### Post by wpshooter on 2009-04-14
What exactly do you mean by "**i figure i can disconnect the cdrom drive**" ?

Are you physically unplugging either the power cable or data cable of the CD-Rom drive at some point during the installation of Ubuntu ?

If you are, why in the world would you be attemping to do that ?

---

### Post by s4mur41j4ck on 2009-04-14
it doesnt have to do with bios settings.

i physically disconnected the drive after install and machine has shut off.

---

### Post by CatKiller on 2009-04-14
Check the jumper on your hard drive (if it's IDE). You might have is set to "Slave, Master Present" which some drives have as an option, and had the CD-ROM drive as Master. If it isn't an IDE drive, or that doesn't help, then I'm out of ideas for the time being. Other than some kind of short or loose connection, since you need to power cycle the PSU to get it to turn on again.

---

### Post by wpshooter on 2009-04-14
Go into Software Sources and uncheck the Ubuntu CD Rom source.  Go in thru safe/alternative mode if need be to get this unchecked.

P.S. - Why would you want to disconnect the CD drive in the first place ?

       You are probably going to find that you need to have this connected, since my guess is that you are going to be needing it in the future.

---

### Post by s4mur41j4ck on 2009-04-14
the cdrom drive does not fit in the mini-itx case i have, so i would like to disconnect it so i can put the side panel back on. i just want this system to be a low power web surfing box

---

### Post by s4mur41j4ck on 2009-04-14
alos no dice on software sources suggestion

---

### Post by logos34 on 2009-04-14
you said

> i would think i was shorting out since it wont turn back on without the power disconnect/reconnect. 

you mean you cycle the power supply switch on the back of the pc or actually remove the power cord?  If the former, try also removing the power cord for ~30 secs--maybe the mobo is 'remembering' some settings for cdrom.  And/or maybe remove the Bios battery on the mobo, or remove/replace the clear bios settings jumper.  But you'll have to recustomize your bios settings afterward.

just a shot in the dark...

---

### Post by s4mur41j4ck on 2009-04-14
thanks but unfortunatly i have pulled the power cord, reset the bios. non of these work, its weird with the cdrom the system boots. without it only gets to starting the os then poof it shuts off

---

### Post by wpshooter on 2009-04-14
Have you tried setting the BIOS parameters back to the load/safe defaults ?

---

### Post by s4mur41j4ck on 2009-04-14
yup to no avail

---

### Post by mc4man on 2009-04-15
If it was a bios issue then you'd never get to the Os load, it would fail the 'post',

Maybe post and or remove all references of the cdrom in your fstab.

---

### Post by s4mur41j4ck on 2009-04-16
finally got a chance to do that, damn job always getting in the way of the hobby.
any no luck i tried removing from fstab and bios. still loading os then instant power off

---

### Post by s4mur41j4ck on 2009-05-06
ok so i finally figured out my problem last weekend. turns out since i am using a compact flash as my hard drive i have nothing drawing on the 12v rail. This is my problem, i remove the cdrom nothing on 12v so the powersupply is designed to shut is self off. apparently there is a minimum amperage, for each voltage line, required or the power supply shuts off to protect it self from failing. so what i end up doing is added a 120mm case fan to keep the box running without the cdrom. this is not permanent but will suffice for now

---

