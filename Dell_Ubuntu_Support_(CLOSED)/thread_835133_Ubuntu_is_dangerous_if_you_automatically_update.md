---
title: "Ubuntu is dangerous if you automatically update"
date: 2008-06-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by keryonic on 2008-06-20
If you installed, like me, Ubuntu in your work computer, you are at risk and you will probably waste precious time when you don't have any.

I have a Vostro 1310 with the Nvidia card and I installed Ubuntu 8.04. After hours of fine tuning, the "only" problem is the mic which doesn't work. I was quiet happy with everything else.

I am a total noob but I want my system to be up to date. So when my system says there is an update file to update, I always say yes.

This morning I said "yes" for an update to kernel 2.6.24-19 then it asked me if I wanted to keep a file called "menu.lst" (or another name, I don't remember) or if I wanted to update it also to the new one. It proposed also to compare the old and the new, I did compare but it is chineese for me. All I want is an up to date system stable and sturdy.I thought the new one would be better.

Now, my Nvidia card is not recognized anymore and the max resolution I can choose is 640x480!!!!!

I am tired of going to fix everything in console, open files or programs I don't understand (Xorg, Xserver, all mysterious programs for me). No I don't remember the model of my Nvidia card (knowing it is an Nvidia is already a lot), I don't remember and I don't want to know what is the max resolution of my 13,1" screen. I just want a system that works, and that will help me work better. I am fed up of searching forums for solutions although I really appreciate all the help I found. I am a linux noob but I know computers much better than any standard person. I am not a fan of any OS, I don't care, I just want something that works and I thought Ubuntu could offer me just what I needed.

Now that I have cried, is there somebody that could help me fix that mess and explain me how I could avoid similar problem in the future. I want to learn but I need to work!

---

### Post by keryonic on 2008-06-20
I lost one hour and of course I found the solution (is it the best one?...I don't know but it works!). But how could an average user (like my mom) have found that solution?

I realized that in etc/X11/ there was a xorg.conf.backup so I just used that file (renamed xorg.conf to xorg.con.bak and xorg.con.backup to xorg.conf).

Now, how could I avoid this in the future (and not spending to much time backing up everything)!!!! There no restoring points in Ubuntu, this is a weakness but maybe there is a better solution that I am unaware of. 

Thanks for any help.

---

### Post by ajgreeny on 2008-06-20
You can always stop the automatic update of your working kernel by using synaptic.  Find out which kernel you are using and is working properly at the moment by typing in terminal ```
uname -r
``` Now search for that kernel in synaptic, highlight it, and then go to to the Package menu and chose **Lock Version.**  The kernel should now stay with the current version and you will not lose your nvidia driver again from using a new kernel.

---

### Post by dlmoak on 2008-06-20
Usually, old kernels are still on your system.  If you hit the 
Escape key when the grub menu comes up, you should be able to choose to boot to your prior kernel.  If you don't have any problems with it and you want to remove the newer kernel you can do it using synaptic.

---

### Post by rickyjones on 2008-06-20
I think the point here is that an update should not break things. This is something I agree with, especially when you are talking about critical things like the display.

I could understand an update breaking a user application in some way, especially if it not a mainstream application (this happens in Windows with some software packages), but an operating system update should never break your display (or networking, sound, etc...).

I would also agree that some sort of simple restoration system would be a great asset. One thing Ubuntu could learn from Windows XP is the "Last known good configuration" boot option. If all the OP had to do was reboot and choose that and it restored the kernel and other settings then he would have been just fine (for the most part).

Sincerely,
Richard

---

### Post by ajgreeny on 2008-06-20
This is one of the good things about Linux Mint, which by default does not upgrade kernels unless you ask it to, and warns of the very problem you found.

---

### Post by keryonic on 2008-06-21
I have repaired my system using an older kernel listed in Grub (2.6.24-17) but how do I do to removed unneeded kernel (2.6.24-18, 2.6.24-19). I have looked in Synaptic but don't know what I should remove.

Any help would be appreciated. Thanks for your answers.

---

### Post by dlmoak on 2008-06-21
Use synaptic package manager.  Search for linux-image and mark for any packages with the number you wish to remove (they should already be marked).  Make sure to leave the one you want to keep on the system.:)

---

### Post by keryonic on 2008-06-21
Thank you. That was easy.:)

---

