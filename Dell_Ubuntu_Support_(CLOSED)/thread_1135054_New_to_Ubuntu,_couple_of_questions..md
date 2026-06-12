---
title: "New to Ubuntu, couple of questions."
date: 2009-04-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by marmaduke01 on 2009-04-24
I have an old Dell Lattitude D620 laptop.  I am downloading Ubuntu 9.04 right now. Would like to give it a try.  Couple of questions.

Once Ubuntu is installed, will I need chipset drivers for the laptop? How would I find them for Ubuntu?

If I'm missing something during the install, (Wi-fi, Bluetooth, sound, video drivers), how would I manually find them?

I read something about "restricted" Drivers. What are those?

I was just reading about defragging in Windows.  Does Ubuntu have a defrag utility?

---

### Post by Big_Croc7 on 2009-04-24
> 
Once Ubuntu is installed, will I need chipset drivers for the laptop? How would I find them for Ubuntu?

Probably not - with a machine of that age it's probable that most things will work straight away (but not certain at all!)

> 
I read something about "restricted" Drivers. What are those?

Most software that is in the Ubuntu repositories is open source.  Restricted drivers are proprietary drivers, usually supplied by the hardware manufacturer as binary-only (i.e. without source code).

> 
I was just reading about defragging in Windows. Does Ubuntu have a defrag utility? 

Not really.  If you use any of the standard filesystem types (ext3, xfs or reiser, as opposed to fat32 or ntfs on Windows) it's all taken care of automatically.

---

### Post by sirebral on 2009-04-25
I have a little experience with Ubuntu now.  I am fairly certain I will not be jumping on the Jaunty train right away.  The main reason is because it can take the developers some time for the OS to get some kinks worked out.  I will probably give the release a few months before making the switch.

Maybe you want to try 8.10 if you have problems with 9.04.  8.10 is pretty stable and has some cool advancements over 8.04 (I love the tabs in Nautilus file explorer - Good call!!)

---

### Post by ad_267 on 2009-04-25
9.04 is pretty stable already and there aren't any huge changes that are likely to cause problems. I'd say stick with 9.04 just because each release gets better and provides better hardware and peripheral support.

You won't need to install any drivers to get things working. If you have an Nvidia or ATI graphics card you can go to System - Administration - Hardware drivers and you can install restricted drivers provided by these companies. With the file system used by Ubuntu you shouldn't need to worry about defragging.

---

### Post by libralibra on 2009-04-26
for D620 and ubuntu9.04, maybe you don't need any configration at all.

It can be used as soon as you install it.

---

### Post by PhrygianCat on 2009-04-26
If you're worried, you should just try running Ubuntu as a live CD before doing any installation. This is the best way to test your hardware.

---

### Post by marmaduke01 on 2009-04-27
> **libralibra said:**
> for D620 and ubuntu9.04, maybe you don't need any configration at all.

It can be used as soon as you install it.


Its installed with a few problems.  During boot up, there is "I/O error" Scrolling down the screen.  But it does boot up into Ubuntu 9.04.  The sound buttons do not work. Even tho I can press the mute button, see the mute icon appear on screen, the sound is not muted.  Also had a awful noise/screech when shutting down Ubuntu.
From what I can see, I only have 3 desktop pictures. All brown.
Finally, while trying to browse with the touchpad, the menu's open up, but when I scroll across with the arrow, the menu's disappear. 

Does this Ubuntu have some kind of "device manager" so I can see if all the drivers installed?

---

### Post by ad_267 on 2009-04-27
> **marmaduke01 said:**
> Its installed with a few problems.  During boot up, there is "I/O error" Scrolling down the screen.  But it does boot up into Ubuntu 9.04.  The sound buttons do not work. Even tho I can press the mute button, see the mute icon appear on screen, the sound is not muted.  Also had a awful noise/screech when shutting down Ubuntu.
From what I can see, I only have 3 desktop pictures. All brown.
Finally, while trying to browse with the touchpad, the menu's open up, but when I scroll across with the arrow, the menu's disappear. 

Does this Ubuntu have some kind of "device manager" so I can see if all the drivers installed?

The I/O error sounds like it could be a hard drive fault. Might be time for a new hard drive soon.

The sound button issue sounds weird, does the volume control application work?

Install the gnome-backgrounds and ubuntustudio-wallpapers packages and look at interfacelift.com for more wallpapers.

---

