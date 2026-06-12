---
title: "Monitor out of range"
date: 2011-06-08
forum: Desktop Environments
---

### Post by Happy Days on 2011-06-08
Upgraded to 11.04 a few weeks ago.  Computer was running fine.  Unity was not capable with the graphics so was running 11 with standard GUI.  All of a sudden, on boot Motherboard splash screen comes up, but as soon ubuntu begins to load, monitor goes Out of Range.  

Works fine with live cd 10.10 though.

Please Help!?

---

### Post by clarkthehardy910mini on 2011-06-13
does anyone have an answer for this?

I'm getting display trouble with a new install of Unity also. No error during installation (took the preview tour of unity while the final files were being copied) It's an old crt monitor, XP loads fine, but ever-since Ubuntu install completed, after choosing Ubuntu from the bootmenu, not even a splash screen comes through, it is an immediate monitor message: 

Attention
Out of range
H:92.5KHz V:58.2Hz

I don't know how to boot to grub or the command line. I don't know how to edit the files in xp, because its in Chinese and I can't read it. So I need help. Thanks for your response.

---

### Post by Happy Days on 2011-06-14
Clarky,  on the bootmenu you should have the option of loading ubuntu in recovery mode.  Can you do this?  What difference does it make?

---

### Post by Khakilang on 2011-06-14
Have you try install the drivers for your graphic card? When I install 11.04 I had to use the Gnome classic and when I install my graphic driver and reboot the Unity comes out.

---

### Post by clarkthehardy910mini on 2011-06-19
No, I can't see the grub2 menu(bootloader), I see something saying Grub loading and then a second later it goes to the the out of range message screen. I can load the Live CD, but can't figure out how to edit my current install.

---

### Post by clarkthehardy910mini on 2011-06-19
> **Khakilang said:**
> Have you try install the drivers for your graphic card? When I install 11.04 I had to use the Gnome classic and when I install my graphic driver and reboot the Unity comes out.

I can't even get Ubuntu to load to command line. How can I do this? The screen goes to "out of range" immediately as grub is loading. One time I had success to get XP to boot up, but it was only after holding down shift and tapping shift and then mashing random buttons on my keyboard for several seconds.

---

### Post by wildmanne39 on 2011-06-20
> **clarkthehardy910mini said:**
> I can't even get Ubuntu to load to command line. How can I do this? The screen goes to "out of range" immediately as grub is loading. One time I had success to get XP to boot up, but it was only after holding down shift and tapping shift and then mashing random buttons on my keyboard for several seconds.
Hi, here is the answer.
```
gksudo gedit /etc/default/grub
```
and change this line:

#GRUB_GFXMODE=640x480

to this:

GRUB_GFXMODE=640x480

Then save and exit the document.
```
sudo update-grub
```
On the display setting you can change them to 800x600 while you are then and it will make the screen look a lot better. But do not change them higher you might get a resolution not supported and not be able to boot.

---

### Post by charlie@pcapps.biz on 2011-11-08
I am a newbie to Ubuntu, so pardon my dumb questions.
I just loaded 11.10 and have the same problem that is being discussed on this thread.
I have been following Clarky's comments and I note that he says that as soon as Ubuntu starts to load, he gets the monitor out of range message and can see nothing else on his screen.  

With this in mind, how is he (or how am I) supposed to enter the commands that are suggested?

CB

---

### Post by mlatelcom on 2011-11-17
when you see the blinking cursor, press the down arrow in your keyboard to boot into the recovery mode, as this option is the second one in the grub menu. you will be able to see the recovery mode. I did it and it worked. you can also try ctrl+alt+F1. I know this is an old thread; but this can help someone else.

---

### Post by CrazyKev on 2011-11-29
> **charlie@pcapps.biz said:**
> I am a newbie to Ubuntu, so pardon my dumb questions.
I just loaded 11.10 and have the same problem that is being discussed on this thread.
I have been following Clarky's comments and I note that he says that as soon as Ubuntu starts to load, he gets the monitor out of range message and can see nothing else on his screen.  

With this in mind, how is he (or how am I) supposed to enter the commands that are suggested?

CB
Assuming that you do finally get to the login screen and then into ubuntu you can run wildmanne39's code in the terminal. Forgive me if you know this but the terminal is found in the accessories list of all your apps. Copy in wildmanne39's code and hit enter and follow his steps and it should work. 

Removing the # from #GRUB_GFXMODE=640x480 makes it run this line so that Grub rums in lower display config.

---

### Post by bryangrant4 on 2012-05-24
I also experienced a very similar thing. Reading through this entire thread, there is nothing here that can remedy the problem.. beyond literally taking out the partition with Ubuntu 12.04 and doing a System Restore from the hidden factory install partition that has the original Windows Vista installation. 

1- How do I correct the screen problem? I can get into the Ubuntu  environment using the kludge described above, so should I use those  commands suggested at this point in a Terminal? 

2- How do I assert the presence of the bootloader? I havent played with  this in years, but back in the day it was a LILO bootloader, and there  was a LILO conf file. Any idea how this works and how to get it to  appear when I reboot the system so a user can select to run Windows? 

Long=winded=gory=details:

I was attempting to setup up this box as a Dual Boot, but the bootloader never appears. Even when I was able to reboot it after installing 300+mb of updates after the install I never saw the bootloader. Then, I shut everything down, went and walked the dogs, booted up, and just Dreadful Silence. 

Booting off the bootdisk gets me back to functioning screen, but.. again, no bootloader, and no way to run Windows any more. Not good. AND, Ubuntu doesnt recongnize there is an existing install of Ubuntu present., even though it was just working a moment before. It finally figures it out when it prompts for partitioning the disk, I quit the install routine at this point, and I can go straight into the installed instance of Ubuntu desktop. 

Responding to some of the suggestions above.. when not using the Ubuntu Boot/Installation Disk, I never do see a cursor, therefore it is not at all possible to interact with the system to enter the suggested commands beyond BIOS settings. 

There is no time elapsed between the Post and when the little message on the monitor appears saying Out of Range, just a extremely brief black screen before the error appears.  

Therefore beyond using the bootdisks  to perform some serious surgery, I am sunk. 

(I am also just a tad nervous about posting this. The last time people seem to have discussed this was back in 11/11. It is now just over 6 months later. )

Thanks. 



2-

---

### Post by bryangrant4 on 2012-05-24
@ Wildemann! 

BTW thanks for that hint. Very helpful. I havent been using Unix in several years.. and handy things like being able to edit a config file as a superuser.. well.. let's just say my memory banks gathered some dust. 


Thanks again. I am still plodding towards a resolution. I will try to document it if I succeed.

---

