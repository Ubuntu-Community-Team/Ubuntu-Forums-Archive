---
title: "Yes, its another laptop heat thread"
date: 2007-08-20
forum: Dell  Ubuntu Support
---

### Post by sunami88 on 2007-08-20
I have a 1.66Ghz (Yonah) CoreDuo, and does the thing ever heat up in Ubuntu. If I'm just surfing around the web or not doing much of anything it ranges from 33 to 40, but the second I start playing a video does she ever heat up. I've seen it go above temperatures of 50 degrees when all the things doing is playing a video. Actually, if I play a high-def video (like the BioShock preview vids), I've seen it hit 62 before I hit stop.

Whats the deal? My harddrive also heats up quite a bit more than it does in Windows (to the touch, Windows has never been able to monitor my harddrive properly). Its almost always at 44 degrees, and after about an hour of playing a DVD off my harddrive I have to pause it for about 10 mins because Im afraid it might fry or something. Forget about setting it on my lap too, its too warm to be comfortable.

I like Ubuntu, and really want to move away from Windows (Im using XP at the moment), but this is getting to be a bit of a deal breaker.

---

### Post by kallistra on 2007-08-20
Have you checked to see if your fans are running? 
 
Even though supposedly the BIOS controls the fans for Dell, mine have not been kicking on without using i8kutils and even then they can only control my left fan... I'm hoping to figure out a fix to get both fans. 
 
I'm using a E1705 btw, so i8kutils might be able to take care of you without problems.

---

### Post by PaganImmolator on 2007-08-20
i8k is the way to go. Its not perfect but now I don't feel like my laptop is going to explode. If you need to, you can manually turn the fans on with i8k.

---

### Post by sunami88 on 2007-08-20
I'll look into i8k. I remember installing it a while back, but I might not have set it up correctly. I'm using an Inspiron 640m.

And I know my fans are running, they just dont kick up higher (like they do in Windows) when under stress. Like I said, I'll give i8k another look.

---

### Post by sunami88 on 2007-08-20
Well i8k seems to have done it. I installed gkrellm, and now I can control the fans etc just the way I like em.

Thanks guys.

---

### Post by saru411 on 2007-08-21
are any of you running 64 bit feisty? if so how did you get i8utils in synaptic? what server do i have to add to repos? do i have to force architecture? 

thanks

---

### Post by Metaljaz on 2007-08-21
this may sound stupid, but i download the i8utils via synaptic but how do i access it. I can't seem to find the program so that i can control my fans.

---

### Post by saru411 on 2007-08-21
are you running 32 or 64 bit?

---

### Post by Kitsun on 2007-08-21
Ive been concerned about my laptops temperature.

It has gotten as high as 70, but it always decreases to about 60 shortly after.

Would temperatures like this damage my laptop?

---

### Post by saru411 on 2007-08-22
this is a SERIOUS ISSUE!!! fan control should be a top priority.

please anyone....help

---

### Post by mtbsoft on 2007-08-22
I tried i8kutils on my Inspiron 9400 but it didn't seem to work at all.  On the one occasion that i8kfan brought a (very small) window up, clicking the contained buttons simply generated an error, the rest of the time I simply ended up with a sleeping task for each time I tried to run it.  I'm beginning to wonder if they've changed the architecture since I've seen reference to the BIOS in other posts but my BIOS contains nothing about the fans at all, unless it's not intended to be user configured.

That said, while I've seen the temp get above 50C and very occasionally over 60C, both fans appear to kick in and bring it back down - I'd prefer to have some more control but it looks like this isn't the way.

---

### Post by saru411 on 2007-08-22
im currently attempting an instalation of lm-sensors threw this link [http://www.lm-sensors.org/wiki](http://www.lm-sensors.org/wiki)

im not a complete noobie but this is above my level of comprehension.  
unfortunately i have school today so i must put off using this wonderful laptop off yet another day. if someone with more experience could help me i would be most appreciative. im stuck after this part

> Which modules should I insert? ¶

sensors-detect will tell you. Take the modprobe lines it recommends and paste them into the appropriate /etc/rc.d/xxxx file to be executed at startup.  

i have this generated

> # I2C adapter drivers
# modprobe unknown adapter NVIDIA i2c adapter 0 at 1:00.0
# modprobe unknown adapter NVIDIA i2c adapter 1 at 1:00.0
# modprobe unknown adapter NVIDIA i2c adapter 2 at 1:00.0
i2c-i801
# Chip drivers
eeprom
# no driver for Smart Battery Charger yet
# Warning: the required module smartbatt is not currently installed
# on your system. For status of 2.6 kernel ports check
# [http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices). If driver is built
# into the kernel, or unavailable, comment out the following line.
smartbatt


the problem is i do not know which file to put it in or what to put there.

thanks to anyone who helps me out, and even those who at least took a look =)

---

### Post by saru411 on 2007-08-22
well, the lm-sensors did not get me anywhere. i found out that my laptop(vostro 1500) does not have sensors. now im working on figuring out how to work on the fans, they run threw acpi. i have gone to my /proc/acpi folder and it has other folders but they are all empty files. i have opened many of them in gedit and all of them are blank files

i'm on my knees begging for assistance

---

### Post by PaganImmolator on 2007-08-23
One thing to understand about i8k because there seems to be some confusion, there is a special gkrellm version that runs i8k. I believe in the respository its 'gkrellm-i8k'.

---

### Post by mtbsoft on 2007-08-28
> **PaganImmolator said:**
> One thing to understand about i8k because there seems to be some confusion, there is a special gkrellm version that runs i8k. I believe in the respository its 'gkrellm-i8k'.

Bingo!  That's it, I now have my fans under full control (manual and/or auto) - there's an excellent thread ([http://ubuntuforums.org/showthread.php?t=2635](http://ubuntuforums.org/showthread.php?t=2635)) that I found once you pointed me to the gkrellm-i8k tool.

Thanks for your help.

---

### Post by hardyn on 2007-08-28
this is probably something that should be built into the kernel, anybody posed it on the launchpad?

---

### Post by mtbsoft on 2007-08-29
One very minor issue I have noticed with GKRellM/i8kUtils is that the fans seem to be the wrong way round on my Inspiron 9400.

When I'm looking at the screen and the right fan is animated it is actually the one to my left that is running - everything else works just fine, speeds, manual override and so on.  It's just a tiny bit annoying - anyone got any ideas how I could swap it over (without having to recode!).  Would you think it would be the i8kutils or the GKrellM folks I'd need to request this change of?

Regarding the fans, I've discovered that the left fan (real left - by the Esc key) is far more efficient at cooling the box down.  With the low speed set at 35C, hysteresis 3, ambient temp. at about 22C, the fan comes on for just one minute before going off again;  the (real) right fan can take up to three minutes to bring the temp. under control and sometime doesn't manage it all without the help of the left.

---

### Post by kansei on 2007-09-07
> **hardyn said:**
> this is probably something that should be built into the kernel, anybody posed it on the launchpad?

+1

any i8k stuff for 64-bit would be much appreciated as well. I don't want to have to use 32-bit *just* so that I don't burn myself and the laptop with this disgusting heat. I'm sick of seeing 70C or higher!

---

