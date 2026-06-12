---
title: "Three finger Gestures to switch workspace and other such gestures with touchpad"
date: 2014-11-11
forum: Gaming &amp; Leisure
---

### Post by nikhil4 on 2014-11-11
Hi ,
I am using Ubuntu 14.04 LTS. I would like to know how can I Achive three four finger gestures to switch workspace and zoom in zoom out , things like these.
It would be great help if any of the member can post the complete procedure to do so .I googled and found few blogs explaning this but those were old and may not work on trusty.

thanks

---

### Post by oldrocker99 on 2014-11-11
What kind of laptop do you have?

---

### Post by nikhil4 on 2014-11-12
@oldrocker99 i use dell laptop Anyways i got it worked below is the way to do achive it.

---

### Post by nikhil4 on 2014-11-12
--------------------------------------------------
In newer systems ( Ubuntu 13.10 and up, Arch, etc.) the version of the xorg input driver shipped no longer supports utilizing gestures using the synclient driver. However, there is a workaround to make this workable. Follow the steps below to install a forked version of the xorg input driver.
Install a Working xserver-xorg-input-synaptics Driver
Ubuntu 13.10, Mint 16, and Up
---------------------------------------------------

First download the following dependencies

    sudo apt-get install build-essential libevdev-dev autoconf automake libmtdev-dev xorg-dev xutils-dev libtool

Now, we need to remove the old driver so the new one will overwrite it

    sudo apt-get remove xserver-xorg-input-synaptics

Then, clone the source and build the new driver!

    git clone [https://github.com/felipejfc/xserver-xorg-input-synaptics.git](https://github.com/felipejfc/xserver-xorg-input-synaptics.git)

    cd xserver-xorg-input-synaptics/

    ./autogen.sh

    ./configure --exec_prefix=/usr

    make

    sudo make install

When this completes, reboot and make sure your pointer works.
Arch Linux

Installation on Arch is much easier. Simply grab the package from the AUR and reboot!
yaourt xf86-input-synaptics-xswipe-git
sudo reboot

Make sure your pointer works as expected after a reboot
Setting up xSwipe

First install the dependencies.
     sudo apt-get install libx11-guitest-perl

Then enable SHMConfig to allow for handling of the gestures.
     mkdir /etc/X11/xorg.conf.d/

     sudo nano /etc/X11/xorg.conf.d/50-synaptics.conf

Fill the file with the following and save it!

 Section "InputClass"
 Identifier "evdev touchpad catchall"
 Driver "synaptics"
 MatchDevicePath "/dev/input/event*"
 MatchIsTouchpad "on"
 Option "Protocol" "event"
 Option "SHMConfig" "on"
 EndSection



Now clone xSwipe to a location of your choose.

     git clone [https://github.com/iberianpig/xSwipe.git](https://github.com/iberianpig/xSwipe.git)

And change the eventkey.cfg file to your favourite Gesture. 
Ignore the ubuntu and gnome sections for unity and cinnnamon.and add your gestures in 'other' part of file.

     cd xSwipe/
     nano eventkey.cfg

Now test by running:

     perl xSwipe.pl

Try to swipe with different gestrues and If they are, you may now add the script to your start up programs depending on your environment. After it is added, reboot and you should have working multitouch gestures!
Enable Natural Scrolling (Optional)

The last step to take is to fix scrolling broken by the SHMConfig. I prefer natural (reverse) scrolling so this is necessary. This step is not necessary if you prefer traditional scrolling. First, create a file called .Xmodmap in your home directory
       cd ~
      nano .Xmodmap

Fill the file with the following to enable natural scrolling. (Note: In mint, this doesnt work in system apps for some odd reason, but in Arch it works fine)
pointer = 1 2 3 5 4 7 6 8 9 10 11 12

Save the file and restart your session. Your trackpad is now all set up!

Update: This seems to take about an hour out of my battery life. To get around this, I change the sensitivity with the parameter -m 30.

Credits:[http://blog.mpiannucci.com/view/multitouchgesture](http://blog.mpiannucci.com/view/multitouchgesture)

---

