---
title: "Wireless Problem"
date: 2005-12-18
forum: General Help
---

### Post by Chris85 on 2005-12-18
Sorry for this, I know there have been various amounts of forumers that post this problem. I have been reading a lot of the threads but I was wondering if anyone could tell me how to install the D-Link DWL-G122, been working on it for quite sometime now (About 3 hours, not long I know :p ) but with no avail.
I am not really familiar with the Linux language so that may be why Im having trouble understanding most other posts. Im learning as I go on :D .

Im really new to Ubuntu and with Linux it self (Started today after giving the LIVE boot a try, saw it was sooo much more stable than Windows, from my part that is). 

Thanks for your patience,

Chris

---

### Post by Chris85 on 2005-12-18
No one? Heh :)

---

### Post by sarah_b on 2005-12-18
[QUOTE=Chris85]No one? Heh :)[/QUOTE]

Welcome to the ubuntu forums Chris85 !

I have a linksys wireless so I would not be much help to you. But there are lots of documentation, starter guides, how-to's, and go to [http://www.ubuntuforums.org/forumdisplay.php?f=101]("http://www.ubuntuforums.org/forumdisplay.php?f=101")
 networking and start looking there, infact maybe you could get one of the moderators to move this post to networking. There are people there that are really good in this category. Also check out the "HOW-TO" category. Just a few suggestions for you, whatever they are worth. 


[http://www.ubuntuforums.org/showthread.php?t=53050&highlight=root+login]("http://www.ubuntuforums.org/showthread.php?t=53050&highlight=root+login")
[http://ubuntuguide.org/]("http://ubuntuguide.org/")

sarah

---

### Post by Chris85 on 2005-12-18
Thank you, it is greatly appreciated :smile:

---

### Post by greenway on 2005-12-18
Hi Chris85,

I just purchased a D-LINK DWL-G122 chipset based USB adapter and installing it went great for me, guess the easiest one I had to install so far.

This is how I went about it:

(I am running Kubuntu 5.04 and a 2.6.14 patched kernel, however I walked a friend of mine through installation on a 2.6.10-5-386 kernel and this also went smoothly)

I am using the latest version of ndiswrapper (1.7) and I don't know I all of this works on the standard version supplied by Ubuntu (0.??). So just to be sure, install the latest version.

Make sure you have the following packages installed:

build-essential (sudo apt-get install build-essential)
kernel-package (sudo apt-get install kernel-package)
gcc-3.4 (sudo apt-get install gcc-3.4)
libncurses5 (sudo apt-get install libncurses5)
libncurses5-dev (sudo apt-get install libncurses5-dev)
libqt3-mt-dev (sudo apt-get install libqt3-mt-dev)

Also, you will have to download the right kernel headers, I will assume you are using the 2.6.10-5-386 kernel:

sudo apt-get install linux-headers-2.6.10-5-386

Now, create a symbolic link to your kernel headers:

sudo ln -s /usr/src/linux-headers-2.6.10-5-386 /lib/modules/2.6.10-5-386/build

Go to the /lib/modules/2.6.10-5-386/build directory and check if the link is there.

Next download the latest version of [ndiswrapper]("http://sourceforge.net/projects/ndiswrapper/") and unpack it (I use the /usr/src/ndiswrapper-<version>) directory.

Now you can compile the source code running first "sudo make clean", then "sudo make" and finally "sudo make install". This should provide you with the latest version of ndiswrapper.

Put the cd provided with the USB adapter in your cd device and go to the directory which contains the driver (you will need the file "netrtusb.inf") and type "sudo ndiswrapper -i netrtusb.inf", this should install your driver. Plug in your USB adapter and type "sudo ndiswrapper -l", this should give the following output:

Installed drivers:
netrtusb                driver present, hardware present

Next, type "sudo modprobe ndiswrapper" to insert the ndiswrapper module. If all went well, the LED on your USB adapter should turn on and you will be ready to use and configure your adapter (using network administrator or iwconfig).

Finally, to make sure the driver is loaded on boot, type "sudo ndiswrapper -m".

If something goes wrong, post it here. This adapter should be quite easy to get to work properly.

grtz
-mattijs

---

