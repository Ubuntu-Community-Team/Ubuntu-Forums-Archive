---
title: "Resolution setting &amp; VGA Mode"
date: 2008-11-15
forum: Desktop Environments
---

### Post by DGZDGZ on 2008-11-15
Hello.

Having set up an old laptop with ubuntu and ran it for the last month or so i decided to begin the switch over by installing it on my desktop. Two instant problems i'm now having are:

1. the resolution's off and none of the settings in the resolution control screen fit the desktop fully (the best i get is 1280x1024 which stretches the last 2inches of the right hand side of the screen)

2. when installing XP on using my graphics card and monitor i always had to enale VGA mode, however the option isn't coming up through the boot menu. I currently have 'nonsupport mode' flashing on the front of my desktop! Is there a way to enable VGA mode from the terminal? (hopefully this sorts out both problems)

I'm running 8.04 & i'm not too sure what graphic card is fitted, but will check if somebody knows how.

Many thanks!

---

### Post by pseudosupport on 2008-11-15
To find what hardware you have run sudo lshw -html >> info.html. That'll put an html document containing the info in your home directory. If you can't open firefox either run it in x or just cut out the >> info.html. That'll display all the contents in your terminal; it just wont be pretty. From there, make sure you have the correct driver installed for your video card, and install the settings manager for the card and work from there.

---

### Post by DGZDGZ on 2008-11-15
I ran the command, but cannot locate the html report.

When i try and install the graphics card through the hardware driver menu, one i click enable i receive the following failure:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx_96.43.05+2.6.24.13-18.41_i386.deb](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx_96.43.05+2.6.24.13-18.41_i386.deb)
  404 Not Found


I take it the this is the deb needed to install my graphic driver?

---

### Post by pseudosupport on 2008-11-15
Do you have the correct repositories enabled? run the command without the >> info.html and find your card there or install sysinfo from the add/remove software app. if you have an ati or nvidia card you can download the deb from their respective site if you can't get it from the package manager.

---

### Post by DGZDGZ on 2008-11-15
Ok here's the update!

I managed to get my graphics driver installed:) but when i restart, i get a totally blank screen with the blue 'nonsupport mode' message flashing. (before i installed the graphics card the message flashed on top of the desktop!)

From previous experience this is solved by enabling VGA mode, which is meant to be done by pressing F8 at start up. For some reason this isn't bringing up the menu (it only brings up the boot device options)

By selecting the original kernel at start up i can get beck into the system without the driver installed. 

Can VGA MODE be enabled from the command line?

---

### Post by pseudosupport on 2008-11-15
I couldn't find a way to enable it in command line I'm going to install another copy of ubuntu in vmware, and work from there. you may want to try sudo dpkg-reconfigure -phigh xserver-xorg, but that will just reset your xorg.conf settings. I'm not sure if that'll do anything or not. Also try a ctrl+alt+f7 from the terminal and see if x starts up for you.

I hope a more seasoned veteran of the forum finds this thread and can come up with something. There's a reason I keep pseudo in front of my name. I'll keep trying, though.

---

### Post by pseudosupport on 2008-11-16
If you could post your xorg.conf file, your card specs, and the driver you installed; it would help immensely. I should have asked for this before, but it slipped my mind.

---

