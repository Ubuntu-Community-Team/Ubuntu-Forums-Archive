---
title: "Which Ubuntu version on m11x and how?"
date: 2010-06-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sephir12 on 2010-06-01
Hello guys,

Primarily I would like to say that I am still a noob with linux.
First thing:
Which version do you reccomend for the m11x? I have been reading countless forums on how the sound doesnt work, that the Alienfx needs tweeking to work etc etc. So far I have seen that the sound problem can be solved with the Realtek driver and that the fx needs a lot of work to fix. The switching between the gfx cards can only be done via the Bios? (I don't really mind the switching part though cause I plan to keep the intel gfx running with linux, since I'll have Win 7 for games n stuff)

Second question:
Is there any risk of messing up the laptop if I dual-boot Ubuntu? I know it's a stupid question, but I saw some posts in the forum where supposedly a guy couldnt even recover to factory settings. 


Third and final question (sorry for tiring you :P)

Where should I start from? I have an external hard drive but no external cd-drive so I am guessing that's the only way I can dual boot the OS. Which version do you recon I download?

thank you and sorry for the long text :)

---

### Post by Sub101 on 2010-06-01
You will need to boot to a flash drive. You can create a bootable flash drive using Windows and would enable you to install Ubuntu as a dual boot.

I am planning on buying an m11x so will be paying very close attention to the thread. 

As I understand it the Sound issue can be resolved using a Realtek driver.

---

### Post by sephir12 on 2010-06-01
Just so that I do not mislead anyone, (as i said i am a bit of a noob) I want to dual boot ubuntu on the machine by using the external hd once (i.e I dont want to have ubuntu only when the hd is connected) 

Thanks and sorry again :)

---

### Post by Bushman87 on 2010-06-18
Hey guys.

I am currently dual booting a m11x r1 with win7 and ubuntu lucid lynx (think its 10.4). 

I asked a friend of mine to setup the partitions for me so I cant really be of much help there. But we did not reformat the hdd completely so theoretically the recovery partition should still be there...

Straight off the bat everything worked except the sound and the wireless. The sound drivers I installed using the instructions in the other m11x ubuntu forum. The wireless drivers i installed from the drivers supplied in ubuntu.

I was to wary to mess with the lighting that i did not bother to fiddle with it. I just use win7 and the current active profile from win7 is active in ubuntu.

One thing i struggled with was grub 2. The dell local safe backup kept rewriting the boot manager so that the grub boot menu didnt load and no operating system could be loaded. There is a better fix here somewhere but i bypassed it by uninstalling the dell local backup.

Just a bit of my experience.

---

### Post by lesterd on 2010-09-01
Hey I have an alienware m11x and I have partioned my space for windows 7 64 bit for room to install Ubuntu 10.4 and that was good. The dell local safe backup keeps rewriting the boot manager so that the grub boot menu didnt load and no operating system could be loaded. I did a supergrub boot to fix it to normal before the installation of ubuntu. You mentioned doing a bypass by uninstalling the dell local backup, but I dont want that to affect my windows backup. You said there was a better fix for this issue? what is this fix? For now I set ubuntu up to run in my windows with visualbox but I really would like it to be partioned...if you could please help me with this I would really appreciate it.

---

### Post by lesterd on 2010-09-04
I figured out a quick and really simple/easy solution to this problem without having to delete or mess with grub at all. The best thing is to logon to your windows OS or which ever you have then download WUBI, this will set everything up for you. This way never messes with the boot drives or grub. The computer boots automatically for windows then it will ask which OS you want to run. This is the best and safest bet!!! Worked 100% for me. Thanks:KS:KS

---

### Post by lutheranpriest on 2011-07-13
I know this is a damn-old thread, but thought I'd throw my $.02 in. I have an m11x R2, and everything works out of the box with Mint 11 x64 (based on Ubuntu 11.04). From time to time, the only problem I have is resuming from sleep state. I'll get it figured out sooner or later.

For the dual-boot problem, I don't have it since Mint is my only installed OS. However, I also don't use the factory hd, rather I'm running my 500gb 7200rpm Seagate. If you want to start all over, you can wipe out all the partitions on your hd, create one partition for win7, install with the recovery dvd, then install ubuntu. You will never have another problem again! That, and you get rid of all the Dell bloatware.

---

