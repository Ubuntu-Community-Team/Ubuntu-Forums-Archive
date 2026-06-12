---
title: "How I Installed BERYL ATI on FIESTY"
date: 2007-05-28
forum: Desktop Effects &amp; Customization
---

### Post by twista on 2007-05-28
Hi,

I've spent about 3 days (apparently my wife says :) trying to get ubuntu fiesty to work with beryl, in my ATI 9600 powered laptop.

After much screwing up, I've finally found something that just made it click altogether!

The magic lies in this [web page]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL")

1. Install ubuntu
2. install envy
3. run envy installing ati driver
4. install bery/emerald etc
5. go to that magic web page and downgrade beryl 0.2.1 which was installed to 0.2.0

Beryl is now just working for me :)

hope this helps...

Twista.

---

### Post by Kent84 on 2007-05-28
This guide worked for me too on my ATI Radeon 9600 pro...
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29)

---

### Post by silent1643 on 2007-05-29
great, anybody got theres working for an x850? i still can't get my desktop effects to work

---

### Post by Kent84 on 2007-05-29
what doesn't work? what are your error messages?

---

### Post by laketechno on 2007-05-29
OK fist go to the synaptics and completely remove all the fglrx driver and eveything that said or talk or smell like fglrx. then look for and install the xorg ati driver. Restart and change ur xorg.conf using 

sudo gedit /etc/X11/xorg.conf 

and there under the device section find the driver and change it to radeon. restart u xserver ctrl+alt+backspace then run all this 

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup.beryl-script

sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup.beryl-script

echo "deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main

deb-src [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main" | sudo tee -a /etc/apt/sources.list

wget [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg) -O- | sudo apt-key add -

sudo apt-get update

sudo apt-get -y install beryl beryl-manager emerald-themes

sudo cp /usr/share/applications/beryl-manager.desktop /etc/xdg/autostart/beryl-manager.desktop

once it finish just restart ur system and enjoy it!

Just remember ur card just have an experimental 3D acceleration not full so for sure u will not be able to run videos over the cube just the cube and all the other beryl effects like transparency and floating windows. Please let me know how working.

---

### Post by silent1643 on 2007-05-29
> **laketechno said:**
> OK fist go to the synaptics and completely remove all the fglrx driver and eveything that said or talk or smell like fglrx. then look for and install the xorg ati driver. Restart and change ur xorg.conf using 

sudo gedit /etc/X11/xorg.conf 

and there under the device section find the driver and change it to radeon. restart u xserver ctrl+alt+backspace then run all this 

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup.beryl-script

sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup.beryl-script

echo "deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main

deb-src [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main" | sudo tee -a /etc/apt/sources.list

wget [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg) -O- | sudo apt-key add -

sudo apt-get update

sudo apt-get -y install beryl beryl-manager emerald-themes

sudo cp /usr/share/applications/beryl-manager.desktop /etc/xdg/autostart/beryl-manager.desktop

once it finish just restart ur system and enjoy it!

Just remember ur card just have an experimental 3D acceleration not full so for sure u will not be able to run videos over the cube just the cube and all the other beryl effects like transparency and floating windows. Please let me know how working.

i assume you know all this because you have the same card?

---

### Post by windows hater on 2007-05-29
whats this envy ??

---

### Post by DeaconSune on 2007-06-01
yeah, nothing on that page mentions envy...so could you help us newbies out on that one?

what is envy, and where do we get it?

---

### Post by DeaconSune on 2007-06-01
ok, so in my haste i neglected to do a google search of envy, in my defence, it's really late right now.  Apparently Envy is a program that detects and installs video drivers for both ATI and nVidia.  and is blazingly simple to use it seems.  So, now that it's done running, i'm going to reboot and see what I can see, or see if i even can see.

it can be found here:
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by fergatron on 2007-06-08
I have a Radeon X850XT as well still cannot get themes to work, in fact installing the driver makes it worse!

---

