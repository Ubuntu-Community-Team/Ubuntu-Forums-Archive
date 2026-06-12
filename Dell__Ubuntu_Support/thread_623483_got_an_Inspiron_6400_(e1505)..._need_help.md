---
title: "got an Inspiron 6400 (e1505)... need help"
date: 2007-11-25
forum: Dell  Ubuntu Support
---

### Post by puffykonez on 2007-11-25
im looking to go from winblows xp to ubuntu, but in order for me todo so, i need to have my WIFI and all my other driver ready to go after install... i know the CD duznt recognize just about everything on my system but does aknowledge it exists, so im wondering where i might find all the nessessary drivers and wut not for my 6400...

much help is greatly appreciated!

THANX!

---

### Post by Skuzniak on 2007-11-25
What wireless card do you have in your computer? If it's a Dell Mini Wireless card, then it is more than likely going to be Broadcom-based. if it is Broadcom based, you can use the bcm43xx drivers through the Restricted Drivers menu for some basic wireless functionality. Have ethernet plugged in on first boot, you should get a window letting you know there are restricted drivers available for your system. Follow through the menus and that will get it up and running for you.

Does your computer use the Sigmatel audio card? Does sound work on the live CD? If not, these instructions may help you.

Open up a terminal and enter the following. Capitalization counts.

sudo gedit /etc/modprobe.d/alsa-base

and add the line "options snd-hda-intel model=5stack" without quotes under the heading # Prevent abnormal drivers from grabbing index 0.



Then the following commands:

sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

You will need your ubuntu disc in your drive for the third command.

Reboot.


When you are more comfortable with ubuntu, following the instructions listed here will get you better functionality, range, signal strength and throughput than the bcm43xx drivers.

Here is the link: [http://ubuntuforums.org/showthread.php?t=297092&highlight=ndiswrapper+howto](http://ubuntuforums.org/showthread.php?t=297092&highlight=ndiswrapper+howto)

Just download the appropriate executable for your wireless card if the 1390 mini card is not the right one for you.

---

### Post by raxso on 2007-11-26
I also have inspiron 6400 and I did not get any problem installing and configuring the devices as long as you have internet connection to perform the updates. for your wireless just follow this thread. I did follow it and my wireless connection is stable.

[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

Cheers and Welcome to Ubuntu.

---

