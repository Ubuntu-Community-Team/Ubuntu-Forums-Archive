---
title: "No sound after Jaunty install (Vostro A90)"
date: 2009-05-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Trygle12 on 2009-05-08
Hello. I am having some issues with sound from both my speakers and my headphone jack after a fresh install of Jaunty Jackalope. Prior to this install, the Dell supplied Hardy distro had sound working right out of the box.

I looked up the issue for about a week now... I can't seem to find anything.
I tried doing what is advised on this page, but I don't seem to be getting any sound.

[http://www.ubuntumini.com/2009/03/fix-audio-in-ubuntu-904-on-dell-mini-9.html](http://www.ubuntumini.com/2009/03/fix-audio-in-ubuntu-904-on-dell-mini-9.html)


When I compare my "lspci -vnn" output to the supplied Mini 9 output in the site, the only difference I see is that my audio device is listed but under capabilities is "[access denied]."

Now the Vostro A90 has been shown to be identical to the Mini 9 in terms of Hardware Specifications, but the fact that this seems to be a Vostro A90 problem might mean that that may not be the case.

If there are any solutions to fixing this issue in Jaunty, please let me know.

...also the little thumbs down demon isn't supposed to be there! I love Ubuntu!

---

### Post by anjilslaire on 2009-05-08
Interesting. Have you gone into the sound settings and turned *everything* up?

Go into Preferences and try adding some more options to turn up the volume.

---

### Post by Trygle12 on 2009-05-08
Yes. I have indeed tried pumping everything to eleven. I still get no sound from the card.

---

### Post by anjilslaire on 2009-05-08
Try booting your Jaunty install media again, be it your CD or from a flash drive, whatever you installed with.

Running from the live environment, can you get any sound from the mixer?

---

### Post by Maheriano on 2009-05-08
Lost my sound too, I'm using Pulse Audio. It worked right after the upgrade but died after a reboot. I'm also using the toslink output on the motherboard.

---

### Post by Trygle12 on 2009-05-08
No. There is no sound on the LiveUSB either.
LiveUSB is on a Sony Microvault 4GB.

---

### Post by Maheriano on 2009-05-08
> **Maheriano said:**
> Lost my sound too, I'm using Pulse Audio. It worked right after the upgrade but died after a reboot. I'm also using the toslink output on the motherboard.

Nevermind me, I just read [this]("http://ubuntuforums.org/showthread.php?t=776958&page=3") thread again to go over the steps I used to get it working last time and realized my volume wasn't set at 0. Once I brought the slider down to the bottom it worked like butter. Carry on.

---

### Post by barney_1 on 2009-05-22
I had the same problem as did several others.  There is a bug report that has a fix for this issue on the Dell Vostro A90.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/368629](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/368629)

Edit the alsa-base.conf
```
sudo nano /etc/modprobe.d/alsa-base.conf
```

Add to the end of that file the following line:
```
options snd-hda-intel model=dell
```

Save the file (ctrl-x) and reboot.  Your sound should now work.

---

### Post by mojomoney on 2009-05-28
Thanks barney_1.  That totally worked on my A90.

---

### Post by bkuebler on 2010-02-15
Thanks Barney, I know that this issue has been around for a while, but that worked perfectly for me as well..

---

