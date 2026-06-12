---
title: "unetbootin troubles"
date: 2009-04-19
forum: General Help
---

### Post by Meow27 on 2009-04-19
ok ive realized something thats getting me very frustrated with this program. 

after some experimentation. i have come to a conclusion that unetbootin cannot make a fat32 medium bootable, only fat16, this means i cant create a livedvd with this program since i require fat32 to fit 4gb into anything at a minimum. 
im assuming unetbootin 319 uses an old version of syslinux. if this is so. can someone link me a simple guide of how to get a new version on my flash drive so i can have a bootable fat32 partition?

thanks in advance

---

### Post by Marikawn on 2009-04-19
Hey Meow,

I recently used unetbootin 319 to install backtrack on my usb drive. What I did to make it fat32 format was I used a windows pc and plugged in the usb drive. When the drive showed up I right clicked and hit format "fat32". See if that helps making your usb into that format. BTW it worked fine, after I set my BIOS to boot from USB Drive.

---

### Post by Meow27 on 2009-04-19
nope i already did that before hand, and did again just too see if i mesed up.

while im replying ill throw in another detail: when my usb is using fat16, the bios recognizes it as a usb media storage, when its in fat32, it recognizes it as a "usb-zip" (it was for older computers that could really boot from usbs smack off the bat) of course, it doesn't boot when its on fat32 (from all of my experiences) with unetbootin thus far

edit--

im classifying my hardware as "dell" since im using different dell computers and some lenovo ones, but the above still applies with all

---

### Post by Mgiacchetti on 2009-04-19
I have had no trouble with fat32 and unetbootin.

---

### Post by Mgiacchetti on 2009-04-19
> **Meow27 said:**
>  when my usb is using fat16, the bios recognizes it as a usb media storage, when its in fat32, it recognizes it as a "usb-zip" 


I would look into this.   and either 1. get a different stick to test with

or

2 get a different make/model pc to try it with, (if that works, try a bios update)

---

### Post by Meow27 on 2009-04-19
> **Mgiacchetti said:**
> I would look into this.   and either 1. get a different stick to test with

or

2 get a different make/model pc to try it with, (if that works, try a bios update)

ive already done that.....

---

### Post by Meow27 on 2009-04-20
bump

---

