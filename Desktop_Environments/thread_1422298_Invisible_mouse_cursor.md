---
title: "Invisible mouse cursor"
date: 2010-03-05
forum: Desktop Environments
---

### Post by ElCoronel on 2010-03-05
Hi everyone!
First, let me tell you i went through a lot of forums and i still can't find a solution so i hope you may help me.

I currently use a laptop (win vista was the original OS) and i decided to get rid of it. So i tried Ubuntu, bam, no pointer, i changed yesterday for Kubuntu and the same problem goes on, invisible pointer. The mouse is perfectly working it's just i can't see it on the screen. To get even worse and make me want to throw my computer through the nearest window, with kubuntu i can't use the same trick as with ubuntu, i mean i can't locate the mouse by holding the 'ctrl' key.

I read on various forums and sites that it's a very common problem with VIA/3 chipsets (which is the one i have) and i also read it's often a bug with OpenChrome and to fix it i may have to modify the xorg.conf.

But here's another issue, my xorg.conf file isn't in the same folder as for most of the people: instead of being in /etc/X11/xorg.conf, it's in /usr/share/X11/xkb/rules/xorg.conf, and, which is most, it ain't even named xorg.conf but xorg! 

Besides, i can't modify the file to enter a command that may be a solution because when i try to save my modifications, it tells me i haven't the permissions and i can't get it to run in root. 

If someone has a solution, even a long and complicated one, please, i'm begging you to help me, i'm starting to get very pissed off at this freaking computer and having to use it blindly with a ghost mouse. 

Thank you very much for the time you spent reading this ans for any help you may provide. 
Have a nice day.

---

### Post by finndo on 2010-03-17
I am having this exact same problem right now.  It just started.  I installed the ATI proprietary drivers 8.7x, VirtualBox 3.14, and OOO 3.2 did a reboot, my display looks normal now (now 1024x768) and my mouse is invisible.  not sure if your "openchrome" is Google chrome, but I am using Chrome as my default browser, but I have rebooted a couple of times since installing it and have not had this problem before.

Going to attempt to change my graphics settings with the ATI catalyst control center and see if the mouse comes back.  As currently to get anything done on my system I have to move the mouse to the bottom and go right and left till the various parts of the plasma bar highlight to let me know where the cursor is and then I have to move it up from there, hoping I am moving straight and click a few times blindly until I get what ever I am trying to hit, like the submit button for this post, versus the preview button...

---

### Post by Royall on 2010-03-18
I just installed my ATI drivers for my Radeon 5770 and have the same problem.

One band-aid remedy is to edit your mouse preferences and check the option so that it finds the pointer for you when you press CTRL

---

### Post by Royall on 2010-03-18
I just fixed my problem by using these instructions

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Install%20the%20fglrx%20Driver%20from%20ATI%20Catalyst%209.12%20For%20Ubuntu%209.10%20Karmic](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Install%20the%20fglrx%20Driver%20from%20ATI%20Catalyst%209.12%20For%20Ubuntu%209.10%20Karmic)

I believe it was probably caused by failing to install one of the packages that the ATI installer generated.

---

### Post by mike1945 on 2010-10-03
I am in need of a link to download to fix my invisible mouse cursor please.

---

