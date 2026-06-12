---
title: "Screen fades with strange colors?"
date: 2008-01-31
forum: Desktop Environments
---

### Post by wantless on 2008-01-31
Hey~
  I'm trying to install 64-bit gutsy on my laptop.  I boot to the cd and it shows all the text stuff when loading, but after that's done, i see a bunch of horizontal grey lines and the edges seem to fade to black and then expands into the center, changing colors as it does, and then once it's all black, it just sits as a black screen and nothing happens.  My laptop is a Compaq Presario F730US with an AMD Athlon X2 64-bit processor.  I have an ext3 partition already set up.  Any ideas?  I couldn't think of any other relevant info, but if there's something else you need, i'll try to find it.  Thanks for the help!!

---

### Post by overdrank on 2008-01-31
> **wantless said:**
> Hey~
  I'm trying to install 64-bit gutsy on my laptop.  I boot to the cd and it shows all the text stuff when loading, but after that's done, i see a bunch of horizontal grey lines and the edges seem to fade to black and then expands into the center, changing colors as it does, and then once it's all black, it just sits as a black screen and nothing happens.  My laptop is a Compaq Presario F730US with an AMD Athlon X2 64-bit processor.  I have an ext3 partition already set up.  Any ideas?  I couldn't think of any other relevant info, but if there's something else you need, i'll try to find it.  Thanks for the help!!

HI and have you checked the cd for errors and Then you may want to do a checksum on the cd 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) 
Also what is the model of the graphics card?

---

### Post by wantless on 2008-01-31
Hey~
  I checked the cd for errors with the boot menu. I'll try it again later on.  My video card is an NVidia GeForce Go 6100.  I haven't tried the x86 version yet though...

---

### Post by wantless on 2008-01-31
The checksum is the same too, btw

---

### Post by overdrank on 2008-02-01
> **wantless said:**
> The checksum is the same too, btw

Ok I have a system with the onboard 6150 and I have seen some issues with the 6100. Have you tried booting the cd in safe graphics mode?

---

### Post by ZanexGt on 2008-02-03
Hey there, I had the same issue. 

Check out [this](http://ubuntuforums.org/showthread.php?t=643195&highlight=F730US) thread. 

I think you might need either of the two boot flags (or both) in order to get your install working. 

1. noapic
2. acpi=off

Let us know if this info helps.

---

