---
title: "Gdm doesn't start anymore after installing the latest nvidia drivers"
date: 2008-05-12
forum: Desktop Environments
---

### Post by trashofmasters on 2008-05-12
Hi, I just tried to install the latest nvidia drivers following a tutorial found on this forum.I installed module-assistant, downloaded a kernel and the drivers from nvidia.com, after stopping gdm I ran:
sh NVIDIA*
the installer started and everything seemed to be ok.
No errors, no warnings, as said in the tutorial, I left the installer to edit my xorg.conf. After rebooting the system GDM couldn't start anymore and now I have to use the recovery. If I try to start gmd it tries to boot twice and then a (visual) prompt ask me to change resultion, but no matter what I choose the system seems to crash (it goes in "OUT OF RANGE")

---

### Post by trashofmasters on 2008-05-12
I edited xorg.conf to use the default video drivers and now I'm able to use the graphical interface again.

But if I enable nvidia restricted drivers I cannot start the gdm.

Should I reinstall the nvidia restricted drivers?

---

### Post by logos34 on 2008-05-12
You could always try [Envy]("http://ubuntuguide.org/wiki/Ubuntu:Hardy#Graphics_cards_and_displays"):

>  A. Latest driver installation with EnvyNG (ATi & nVidia)

Read first this faq: [http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A)

Open a terminal and type :

 sudo apt-get install envyng-gtk

After rebooting, drivers should be installed and working. 

---

### Post by trashofmasters on 2008-05-12
Thanks for the reply, I'll try your solution.
I hope it will works :P

---

### Post by Xiong Chiamiov on 2008-05-13
See [this post]("http://ubuntuforums.org/showpost.php?p=4946921&postcount=10"), linking to a few others.  It has to do with a fix that NVIDIA put in the latest beta.

---

### Post by gnivler on 2008-05-13
> **trashofmasters said:**
> Hi, I just tried to install the latest nvidia drivers following a tutorial found on this forum.I installed module-assistant, downloaded a kernel and the drivers from nvidia.com, after stopping gdm I ran:
sh NVIDIA*
the installer started and everything seemed to be ok.
No errors, no warnings, as said in the tutorial, I left the installer to edit my xorg.conf. After rebooting the system GDM couldn't start anymore and now I have to use the recovery. If I try to start gmd it tries to boot twice and then a (visual) prompt ask me to change resultion, but no matter what I choose the system seems to crash (it goes in "OUT OF RANGE")

You might want to check Synaptic Package Manager, for any nvidia-glx packages that are installed.  I had some issues using downloaded drivers from nvidia.com conflicting until I was more thorough and cleaned up first, iirc my symptoms were similar to what you are describing.  I think there was a wiki article on it but I can't seem to find it right now, but I think the important part was removing those packages (and rebooting).

---

