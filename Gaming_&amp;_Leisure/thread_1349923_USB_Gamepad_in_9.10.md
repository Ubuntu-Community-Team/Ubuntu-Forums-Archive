---
title: "USB Gamepad in 9.10"
date: 2009-12-08
forum: Gaming &amp; Leisure
---

### Post by Valpskott on 2009-12-08
I can't get my USB gamepad to work in 9.10 Karmic Koala. I have a PS2 controller which I connect via a USB adapter, it worked fine in 8.10, auto detected it an all. Researching the problem led me to a guide that said I could install 'joystick' and 'jscalibrator', the first didn't do the trick and the latter wouldn't install since it was missing from the repositories.

Is this a common problem in Karmic Koala?

Any fix?

---

### Post by elconsulto on 2009-12-08
it looks like it's because they dropped jscalibrator from 9.10, i'm actually trying to get this to work as well, i'll post if i find anything.

---

### Post by Valpskott on 2009-12-09
Ahh, great, keep me posted if you find anything and I'll do the same :)

---

### Post by gokussj4nr on 2009-12-10
Also trying to get this to work with no luck so far.  Will post if I find a way :)

---

### Post by Valpskott on 2009-12-11
I got it to work, and this is how I did it.

I installed Jaunty on another Partition. Setting up Jaunty and Karmic to share the same /Home partition. Then I configured the Gamepad using jscalibrator and then the "sudo chmod 666 /dev/input/js0" command in terminal. Looking through the Terminal commands I've used I also find "sudo modprobe analog" and "sudo modprobe gameport", don't know what it does, but it can be part of the fix.

Now when I boot up in Karmic, the gamepad works.

But to be frank, I do not know why it works in Karmic, since the /Home partition doesn't contain the "/dev/input/" directory(it belongs to the root of each system which are on two seperated partitions).

Maybe there is a easier work around... but It's hard for me to test for another solution, since my Karmic now has a working js0 in "/dev/input/" everytime I boot.

You could always try the commands I've listed directly in Karmic Koala.

jscalibrator won't work, but the following could make a diffrence.

> sudo modprobe gameport
sudo modprobe analog
sudo chmod 666 /dev/input/js0

I tried these commands several times, so, I don't know the correct order(if that even matters). If it works, please let us know. You know you're on the right track if you get a "js0" in your "/dev/input/" directory.

---

### Post by azurplex on 2010-01-29
Since you calibrated your stick/pad in Jaunty and It shares the home folder with Karmic, The calibration file will be in your home directory on both.
You can see/find it by opening the file browser and going to Edit> Preferences and check "show hidden and backup files". Once you find it you can make it part of your regular backup so you'll always have it.
You do regular backups at least your home directory don't you?

---

### Post by azurplex on 2010-01-29
I'm also noticing that my usb gamepad shows up as /dev/hidraw3 with a link to it from /dev/input/js0 because pads/sticks are "Human Input Devices" like mice and keys.
I'm thinking maybe a link to it from /dev/js0 may help certain games that look for input there might help.
Or perhaps we need to link to the calibration file too somehow.
I'm still fiddling with it.
A gui for joystick would be nice.

---

### Post by azurplex on 2010-01-29
[http://ubuntuforums.org/showthread.php?t=1175430](http://ubuntuforums.org/showthread.php?t=1175430)

Some commands in this post may help.

---

### Post by Chuckylarms on 2010-02-02
Ok, could someone please explain this to a complete Ubuntu rookie? My Windows went FUBAR, so I jump on the free wagon to Linux-ville. I don't have the previous version of Ubuntu, so could someone walk me through how to get my joypads working? A joyless life is just not worth living.

~Chucky Larms

---

### Post by Wild Wallice on 2010-02-02
I too have a problem on this front, I originally posted a thread about it here: [http://ubuntuforums.org/showthread.php?t=1384109](http://ubuntuforums.org/showthread.php?t=1384109) but that thread didn't get any replies at all.  Back when I first tried Ubuntu on version 9.04, I used jscalibrator to make my sixaxis ps3 controller work. Now that jscalibrator has been removed in 9.10, I've tried to make due with jscal on my recent ubuntu install on my laptop, only to have jscal not work in any way, shape or form. "jscal -c /dev/input/js0" gives me a segmentation fault which prevents me from calibrating it, which in turn gives me phantom inputs whenever I try to play something with it.  Does anyone have any idea why I am getting segmentation faults and how to fix this?

---

### Post by mojorising5150 on 2010-02-09
Yeah, just got a chillstream and the Ubuntu is being a hooker at the moment, sleeping around with my mouse and keyboard but wont even give my chillstream a quickie.... what's up with that!? I tried using this [https://help.ubuntu.com/community/Joystick_lshal_outputs_done](https://help.ubuntu.com/community/Joystick_lshal_outputs_done) by downloading the logitech_chillstream.fdi then moving it to policy via sudo nautilus but i get nothing... I'm stumped....

---

### Post by Mareritt on 2010-04-11
Ok guys, I think I got it. (Atleast if you are trying to get the gamepad working in snes9express)

In snes9express the default controller directory is set to /dev/js0 

Go to /dev/input  -> re-connect your gamepad and js0 should appear in that folder.
In snes9express set /dev/input as default dir. and you're good to go :)

---

### Post by ngrieb on 2010-08-09
Changing the permissions of /dev/input/js0 worked for me. It also seems that the devices have been moved from previous versions from what I gather online (moved from /dev/js0 to dev/input/js0, but I could be wrong). 

The problem is now that I have no idea what the absolutely terrible jscal is trying to get from me. Am I supposed to move the joysticks to till the number is the maximum value? It also says I have more than a 3 axis gamepad, which is odd cause it's a Phillips PS2 style controller.

---

