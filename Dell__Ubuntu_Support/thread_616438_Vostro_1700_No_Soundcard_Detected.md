---
title: "Vostro 1700 No Soundcard Detected"
date: 2007-11-18
forum: Dell  Ubuntu Support
---

### Post by Squirrel Ninja on 2007-11-18
So here's what I've tried so far,
```
aplay -l
``` returns no sound card detected.
```
lspci -v
``` returns Intel Corporation 82801H (ICH8 Family) HD Audio Controller
as my sound card

I tried running ```
sudo apt-get install linux-backports-modules-generic
``` but the update didn't help and I wasn't able to download ```
sudo apt-get install linux-backports-modules-i386
```

I also ran through the steps in [http://ubuntuforums.org/showthread.php?t=205449&highlight=no+sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=no+sound)
but that didn't help as there seems to be no asla drivers for my card.
If anyone could please help me out I'd really appreciate it, and also please explain whats required in the steps as I'm still very new to linux
Thanks -SN

---

### Post by soapytheclown on 2007-11-22
any luck with this yet m8 i had the same problem when i used the live cd and now im fed up with trying to use vista its time to put ubuntu on this laptop, the only problem being sound n webcam but ive seen the fixes for the cam about the forum, i tried the same things u tried when i used the live d to no avail either

---

### Post by jfbaro on 2007-11-29
I am having the same problem about the sound card! :(

anyone?

---

### Post by Skuzniak on 2007-11-29
Try the following. These are the instructions I posted for my Vostro 1400, I believe all of the Vostro's (minus the 1000) use the same card.

sudo gedit /etc/modprobe.d/alsa-base

and add the line "options snd-hda-intel model=5stack" without quotes under the heading # Prevent abnormal drivers from grabbing index 0.



Then the following commands:

sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

You will need your ubuntu disc in your drive for the third command.

Reboot.

---

### Post by jahabdank on 2007-11-30
Hello,

for me the above instruction did not work, but I have solved the problem with the following steps (very unprofessional way, but worked for me, so is good enough - any of the good guys - please expand, what actually have happened :)

1) Reinstall Ubuntu to the 7.1 (that is one of the points that should be expanded :) - have the network connection on while installing. It will automatically get the updates (and here again - I do not know which update fixes it, and even how to get the updates not via automatic updates :).

2) install all the automatic updates (in my case 93 of them :)

3) thanks to the updates, the problem with nVidia gforce 8500 was fixed as well.

4) follow the instructions from:
[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)
I took the method G.

This does not solve the problem with the not working microphone - but at least the sound is ok. I have to add that without the updates, I could not fix it.

Hope that it helps anyone. Cheers,
Jozef

---

### Post by jfbaro on 2007-12-01
[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

I used the item G there and it worked just in the first reboot, after that I didn't work anymore.

I am using Kubuntu 7.10... what could I do to solve that problem once for all?

Thanks guys!

---

### Post by pingnak on 2008-04-26
With Hardy/8.04, the 64 bit version worked out of the box, and the 32 bit version I had to install the 'linux-rt' package through Synaptic Package manager and boot that kernel, and it worked fine.

This is where the bug's being reported on Hardy, and where I found the fix.
[https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/211644](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/211644)

---

