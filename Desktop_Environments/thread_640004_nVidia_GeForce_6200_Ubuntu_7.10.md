---
title: "nVidia GeForce 6200 Ubuntu 7.10"
date: 2007-12-13
forum: Desktop Environments
---

### Post by Bob Bobbio on 2007-12-13
I have installed an AGP nVidia GeForce 6200 graphics card in my 3.0Ghz athlon machine that was runnig ubuntu 7.10.  When it started up into Ubuntu it gave me the restricted drivers manager and it installed the nvidia driver and restarted, but when it restarted, after it got through the Ubuntu loading screen it just goes black and nothing happens.  I can't seem to get a terminal either using ctrl-alt-f2 or any of the f-keys, no response at all.  I started up in the recovory kernel and reconfigured the xserver (with the sudo dpkg-reconfigure xserver-xorg) to the best I could selecting nVidia on the first screen.. but still the same result.  Thank You.

---

### Post by bistros on 2007-12-13
Try (as root) in a console session:

nvidia-glx-config enable

If the nvidia driver is install, but not enabled you get results like you've seen.

---

### Post by SolusNunquam on 2007-12-13
make sure you have the correct refresh rate and res if an out of range error occurs. That was one of my problems...

---

### Post by Bob Bobbio on 2007-12-18
I tried both of those, but they didn't work, thanks for your responses, anymore suggestions?
I start xserver and it goes black and it doesn't respond.

---

### Post by Dougo007 on 2007-12-18
I ran this OS (desktop version) from a CD and my display did not work correctly.

Before I loads the OS it gives me boot up options such as changing various settings.

I selected VGA and changed the setting from "VGA" to the closest display that I use on MS Windows XP.

I hope this is of some help.:)

---

### Post by feenicks on 2007-12-19
I don't know how much help this will be.  I've only just finished my first Ubuntu install this week.  Yesterday I got the graphics sorted out thanks to the forums.  My problem was that the GUI wouldn't even start with the card in the slot (GeForce 4000 MX).

When GRUB first flashes by during the boot sequence, hit ESC and pick recovery mode to get the root prompt.  From there type dpkg-reconfigure xserver-xorg and go through the steps.  On mine I let it autodetect pretty much everything.  It selected the right card.  The video driver to use though is "vesa" just so you can get into the GUI properly.  After it boots back up you'll be at a low resolution.  Make sure the drivers are downloaded (I used synaptic) and then enable under the Restricted drives menu.

The key for me was running the xserver from root during boot.

If you want help from a noob you can PM me.  Good luck!

---

