---
title: "Live CD Refuses to boot"
date: 2006-07-23
forum: Desktop Environments
---

### Post by Knelland on 2006-07-23
G'day, downloaded the live CD of Ubuntu 6.06 (i386) over BitTorrent.

I burn it to disc, plop it in my boot drive, reboot. Get to the first boot screen, select startup/install and it does some complex-lookin' things before giving me a blank black screen with "Uncompressing Linux... Ok. Booting kernel" with a flickering cursor like an underscore_ symbol underneath it, at the top. I waited and waited and waited and still nothing happened. I repeated this a number of times, same results.](*,)  I also checked the CD for defects.

Am running Windows XP, 512 MB of RAM, on an 1.66Ghz AMD chip with a Radeon 9600 graphics card.

Any suggestions? I am quite frustrated as I wanted a taste of a non-windows OS and Ubuntu seemed like a good place to start.

---

### Post by loell on 2006-07-23
have you check the md5sum before burning the cd?

---

### Post by Knelland on 2006-07-23
What is that and how do I do it?

---

### Post by loell on 2006-07-23
just do

md5sum filename.iso

if it matches with that from ubuntu.com then the file is not corrupt.
and if its not corrupted then, your burned cd is ok.

---

### Post by loell on 2006-07-23
e2e5e0bfb2edffd2ce02dd77bda4558e  
this is the md5sum of ubuntu-6.06-desktop-i386.iso

---

### Post by Knelland on 2006-07-23
"md5sum filename.iso"
How? I have tried the windows command line in the directory of the iso file, it doesn't recognise 'md5sum' as a command

---

### Post by Knelland on 2006-07-23
Wait, found a little application that does md5sums, and they are the same. Hmmmmm.

---

### Post by loell on 2006-07-23
oh sorry, i forgot that you're in windows

you can download the md5sum utility in

[http://downloads.activestate.com/contrib/md5sum/Windows/]("http://downloads.activestate.com/contrib/md5sum/Windows/")

---

### Post by loell on 2006-07-23
if they have the exact md5sum from the above post then your cd is ok

this might be hardware related..

---

### Post by bikeboy on 2006-07-23
Did you try booting with the safe graphics mode? I found this necessary with my ATI 9250 on several version of linux.

---

### Post by Knelland on 2006-07-24
Tried the safe graphics mode, still no change. Tried a different CD, again, no change. Thanks for the help anyway

---

