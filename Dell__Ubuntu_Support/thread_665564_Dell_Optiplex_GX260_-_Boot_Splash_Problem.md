---
title: "Dell Optiplex GX260 - Boot Splash Problem"
date: 2008-01-12
forum: Dell  Ubuntu Support
---

### Post by sreek007 on 2008-01-12
Hello everyone! :)

I am completely new to Ubuntu... So, please bear with me... :(

After a lot of hurdles I have finally completed the installation of Ubuntu 7.10 (Gusty Gibbon) on my Dell Optiplex GX 260 Desktop... :KS

The only problem is with the Boot Splash... I looked around the forum a lot and launchpad but, I could not solve the problem...:mad:

I tried changing the resolution from /etc/usplash.conf...But, no use...:|


Here are my Desktop's specifications...

Dell Optiplex GX 260

Processor - Intel Pentium 4 2.4 GHz
 
Chipset - Intel 845G

Graphic Processor - Intel Extreme Graphic

Hard Drive Capacity - (25 GB <XP>)...(15 GB <Ubuntu>)
 
Installed Memory - 256 MB (DDR SDRAM)



Hope someone can help me regarding this issue...Thanks a lot...:grin:

---

### Post by sreek007 on 2008-01-13
Can Someone Please help...???

---

### Post by Omnios on 2008-01-13
There i a boot splash how to under slow or no boot. 
 
 From above you have not provided a lot of information pertaining to your problem. What exactly is the problem?
No boot splash?
There is a fix for this.
Is it log in?
Xserver likes using the highest res for the log in.
 
 Please identify the problems you are having.

---

### Post by sreek007 on 2008-01-13
Thanks for the reply...

The problem is...I don't see Ubuntu's Boot Splash Screen...

When I select, Ubuntu from my GRUB list...My screen just goes blank until I get to the login  screen...

I just don't want to stare at a blank screen while booting into Ubuntu...

I want to fix it so, I can see the boot screen...

---

### Post by Omnios on 2008-01-13
> **sreek007 said:**
> Thanks for the reply...
 
The problem is...I don't see Ubuntu's Boot Splash Screen...
 
When I select, Ubuntu from my GRUB list...My screen just goes blank until I get to the login screen...
 
I just don't want to stare at a blank screen while booting into Ubuntu...
 
I want to fix it so, I can see the boot screen...
 
 this thread shows whare to modify the bootsplash res and had been mentioned in other posts. This should fix your problem once a supported res is inputed for bootsplash.
 
 [http://http://ubuntuforums.org/showpost.php?p=3741687&postcount=21](http://http://ubuntuforums.org/showpost.php?p=3741687&postcount=21)

---

### Post by bodycoach2 on 2008-01-14
The Dell GX260 BIOS is probably set to a frame rate of 1mb. Change that to 8mb in the BIOS, save, and restart.
We have several GX260's, and this was a problem till we figured that out.

Also, I suggest installing a graphics card in the machine. An Nvidia 128 mb type will be fairly inexpensive, and work just fine with compiz.

---

### Post by sreek007 on 2008-01-14
> **bodycoach2 said:**
> The Dell GX260 BIOS is probably set to a frame rate of 1mb. Change that to 8mb in the BIOS, save, and restart.
We have several GX260's, and this was a problem till we figured that out.

Also, I suggest installing a graphics card in the machine. An Nvidia 128 mb type will be fairly inexpensive, and work just fine with compiz.

Thanks a lot...:)

I changed it and it worked like a charm...;)

---

### Post by bodycoach2 on 2008-01-17
Admins - Please mark 'Solved'

---

### Post by luvit on 2008-03-13
You guys may be beyond this, but I had pure success with GX260 having optimal video. Heres what I did:

I downloaded the alternate ISO and it solved my video problem on my GX260.  I now can leave my BIOS at 256MB Video RAM _and_ have 1024x768 75Hz refresh rate.

]For reference I viewed my display settings:
  System>Administration>Screens and Graphics - Graphics Card Tab - Driver: intel Experimental modesetting driver for l...

Before I installed Ubuntu I upgraded my BIOS which may have contributed to my fantastic video success. You can get the BIOS update from my blog. Lemme Know!

---

