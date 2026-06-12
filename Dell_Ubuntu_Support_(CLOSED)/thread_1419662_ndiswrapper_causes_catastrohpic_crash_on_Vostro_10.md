---
title: "ndiswrapper causes catastrohpic crash on Vostro 1000 running Karmic?!"
date: 2010-03-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by laptendo64 on 2010-03-02
Hello y'all.  I just reformatted my Dell Vostro 1000 with the 64-bit version of Karmic but when I use ndiswrapper to enable my broadcom wireless card, the system completely crashes and on subsequent reboots will only start up in console mode.

I used these commands in the terminal, which I got from [here](http://ubuntuforums.org/showthread.php?t=297092&highlight=ndiswrapper+broadcom+1505).
```
sudo rmmod ndiswrapper
sudo ndiswrapper -e bcmwl5
sudo apt-get remove ndiswrapper-utils

sudo apt-get update
sudo apt-get install build-essential
sudo apt-get install linux-headers-`uname -r`

sudo -s
echo blacklist bcm43xx >> /etc/modprobe.d/blacklist
exit

cd YOUR-NDISWRAPPER-DIRECTORY
sudo make uninstall
sudo make distclean
sudo make
sudo make install

cd YOUR-DRIVER-DIRECTORY
sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -l

sudo -s
echo ndiswrapper >> /etc/modules
exit

```

I used the same how-to guide to setup my wireless on the same computer running Intrepid and Jaunty and it worked more or less perfectly.  On Intrepid and Jaunty, after doing the ndiswrapper stuff in the command line, I would have to go to the restricted drivers box on the admin menu and enable the restricted Broadcom driver.  After doing that the wifi light would come on and I could detect and connect to networks.

This time with Karmic I get through all the steps that I just described, and my wifi light will come on and I'll see available networks on the network menu and it looks like everything's working OK. And then the GUI completely crashes.  The first time this happened, when I tried to reboot I got some message about "kernel panic" and I couldn't get any further.  I reinstalled from the live disc and completed the same steps and had another crash, but this time I can only boot up in console.

I'm not very knowledgeable but basically I'm trying to find out if there is a solution for this bug or is this problem indicative of something more serious?  Should I install a more stable version like 8.04?

---

### Post by coffeeaddict22 on 2010-03-05
Hi,
In short, no. 


Broadcom make a bit of plastic and metal, designed to convert electrical signals to radio waves.  They _also_ write the software that talks to it and translates that signal into something your operating system can interpret, and that talks to your operating system.  That's the driver.

For many years, wireless modems were largely "unsupported" (read "didn't work" ) in Linux.  The first workaround was to mimic the bits of the MS operating system needed to make the driver work, and 'wrap' the Windows driver, essentially translating it's messages to and from the Linux kernel: that's ndiswrapper.  To use ndiswrapper, you downloaded the Windows driver, processed it and then sent it to ndiswrapper, which would run it inside a "shell" that hid the Windows code from a Linux system.

Currently, the company itself has written a Linux driver; the source is not open to view, so it cannot be included in the installation by default.  That's the restricted Broadcom driver (While it's no worse than any Windows driver, companies before now have delivered drivers that "phoned home" without the users knowledge, and it's that sort of behaviour that has driven the open source approach).

What you describe is getting two drivers for the same card.  It's a pretty good strategy for carnage, but not for working wireless.  Your best bet is to uninstall ndiswrapper.  Install the restricted drivers and you should be away. 

Post back if you need more help.

---

