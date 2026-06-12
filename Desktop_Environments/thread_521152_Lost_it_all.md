---
title: "Lost it all"
date: 2007-08-09
forum: Desktop Environments
---

### Post by nanogeek on 2007-08-09
About a week ago I set up Ubuntu 6.10 on a Pentium II platform. 

With a little help, I was finally able to connect to the Internet by networking it with my Windows XP machine and using the XP's internet connection with ICS. ( I connect to the inernet from the XP-box via a USB DSL modem which doesn’t work with Ubuntu.) The machines are networked directly with a crossover network cable.

The first thing I did was update all programs. 

When the process completed _everything_ was gone.

I now have a screen with two white bars, one at the top, one at the bottom, and in between the pretty Ubuntu orange background. On the top line is the Keyboard indicator, telling me my USA keyboard is active, and a master volume control. Nothing else. No “Applications”, no “Places”, no “System”, nothing. Not even the Start/Stop Button on the right. On the bottom is the recycle bin. Nothing else. I can toggle the keyboard to its second layout. I can adjust the volume. I can right click the desktop and get some options including "Create Launcher" and “Create Folder”.  I can create a folder and from it access the file structure and even launch OpenOffice by selecting a document file.

How do I restore the original setup?
If the answere includes doing things in Terminal, how do I start Terminal since I can’t select Applications->Accessories->Terminal?

With Windows I would bless Bill, do the three fingered salute and reboot.
I somehow doubt that this would help here, and as I understand it the beauty of Linux is that it just keeps going, without the need for a reboot. 

Can someone help me out here?

TIA

---

### Post by ruibernardo on 2007-08-09
Hi nanogeek,

can you try to boot to your previous kernel on boot? If you don't see the GRUB menu on boot, keep pressing "Esc" while the computer boots to see it. Then select the previous kernel version.

About the terminal, if you can't access the Gnome menu, you always can access the tty consoles by pressing Alt+Ctrl+F1 and login.

Cheers

---

### Post by nanogeek on 2007-08-09
Thanks for your suggestion. I will try it. Just one thing, what does "boot to your previous kernel"  mean?
I am one very green bean.

nanogeek

---

### Post by ruibernardo on 2007-08-09
Try pressing "Esc" while the computer boot, it should become very clear when the GRUB menu appears. :)

Cheers.

---

### Post by nanogeek on 2007-08-09
Reboot solved the problem. Not elegant, but effective.
Thank you.

---

