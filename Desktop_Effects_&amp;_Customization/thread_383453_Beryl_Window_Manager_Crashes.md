---
title: "Beryl Window Manager Crashes"
date: 2007-03-13
forum: Desktop Effects &amp; Customization
---

### Post by steve101101 on 2007-03-13
Hey, I just installed Beryl and got the legacy nvidia drivers for my Nvidia MX440 AGP card. Beryl installed fine, however if i change the default window manager from gnome to beryl it just switches back to gnome. 

Also when i typed this:

glxinfo | grep direct

I get:

direct rendering: no

please help.

---

### Post by steve101101 on 2007-03-13
I installed the 96.31 drivers for the card.This then allows beryl to be activated. However when i rebooted the system the x session would not start. to fix this i did this

```

sudo nano /etc/default/linux-restricted-modules-common

```

looked for the following line 

DISABLED_MODULES=""

and added nv between the quotes. its working now.

---

### Post by gmc1200 on 2007-03-13
Hey Steve,

You might've seen my other post, but i just wanted to ask you a question.  I'm trying to do exactly what you just did, but I can't get the drivers to install correctly.  Could you run down what you did to get it installed and get beryl working?  I have the same video card as you.

Thanks!

---

### Post by steve101101 on 2007-03-13
Quote:
Originally Posted by gmc1200
Hey Steve,

You might've seen my other post, but i just wanted to ask you a question. I'm trying to do exactly what you just did, but I can't get the drivers to install correctly. Could you run down what you did to get it installed and get beryl working? I have the same video card as you.

Thanks!
I used the 96.31 nvidia driver from [www.nvidia.com](www.nvidia.com). i then followed the instructions found here [http://wiki.beryl-project.org/wiki/I...gy_with_nVidia](http://wiki.beryl-project.org/wiki/I...gy_with_nVidia)

then follow this section....

If problems with an installation with an official package occur

After the installation of the official nVidia package, it is possible (though perhaps unlikely) that X11 will refuse due its attempt to utilize the older version of the nVidia kernel module. In such a situation, you should unload and subsequently reload the nvidia kernel module by running:

sudo rmmod nvidia && sudo modprobe nvidia

In the case that the user receives an API mismatch error upon restarting Ubuntu, it is necessary disable the "nv" module. To simultaneously backup linux-restricted-modules-common and automatically disable the nv module, you may execute:

sudo cp /etc/default/linux-restricted-modules-common /etc/default/_linux-restricted-modules-common.backup && sudo sed -i -e 's/^DISABLED_MODULES="/DISABLED_MODULES="nv /' -e 's/ "/"/' /etc/default/linux-restricted-modules-common

Or, to simultaneously backup linux-restricted-modules-common and edit the file manually, run:

sudo cp /etc/default/linux-restricted-modules-common /etc/default/_linux-restricted-modules-common.backup && sudo nano /etc/default/linux-restricted-modules-common

and add "nv, " the following line:

DISABLED_MODULES="nv, [...]" # Edit only this line.

[edit]

mainly do the last line adding "nv" without this the x session would not start. you may need to boot into the recovery mode at the bootloader. and use the shells in gnome <Ctrl+Alt+F1>.

Hope that helps.

---

### Post by gmc1200 on 2007-03-15
Hey Steve,

Thanks for the help, unfortunately, it didn't work.  I had my hopes high only to be shot down.  Again, thanks for the reply.

---

### Post by Masterj15 on 2007-03-15
O I will help. I have not install beryl either but You must be one step ahead of me. Type in the terminal nvidia-xconfig and that should make your Xorg apart of the nvidia you can tell if you did it right by pressing Alt+F2 and run
gksudo gedit /usr/bin/startxgl

Then if they telk about nvidia first then you did it.

That is one way to try and get direct rendering.
You need direct rending for beryl.


I have a Nvidia Tnt2/tnt2 pro

---

### Post by gmc1200 on 2007-03-15
Hey i tried that out, didn't work.  I think im just having a problem using the drivers.  I can install the 96xx drivers, but when ever i try to boot up the x server, its a blank screen.  I dont know what's the deal.

---

### Post by steve101101 on 2007-03-17
I dont know why that did not work. It worked for my MX 440.

---

### Post by Masterj15 on 2007-03-17
Have you tried the .deb packages or the run. Try both if you haven.

---

### Post by gmc1200 on 2007-03-20
I used the nvidia script on their website. version 9631 I believe.  I've also tried envy.  The thing is, they install just fine.  The problem is, correct me with wording and terminology because I know its wrong, x wont start unless I use the "nv" drivers

---

### Post by steve101101 on 2007-03-20
thats correct. that is what i have to do BUT it works fine. trust me.

---

### Post by gmc1200 on 2007-03-21
I figured out how to fix my problem.  It was my monitor that was messing things up.  Look at this thread to see what I did: [http://www.ubuntuforums.org/showthread.php?t=381174](http://www.ubuntuforums.org/showthread.php?t=381174)

---

