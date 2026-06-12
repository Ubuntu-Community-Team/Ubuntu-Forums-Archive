---
title: "Problems with PulseAudio"
date: 2009-03-19
forum: General Help
---

### Post by Peasantoid on 2009-03-19
Here's a quick summary of my problem.

I just purchased a Bluetooth headset and got it to work after a sleepless night of hackery. However, I was stumped by the fact that it would only emit this awful scratchy burping sound. After troubleshooting for several hours, I realized the weak link wasn't the device (I could play to it with a command like "mplayer -ao alsa:device=btheadset /path/to/file.wav"), but the sound server &#8212; PulseAudio. It, uh...it no worky.

Is there a less sucky sound server out there (one that supports redirection to devices)? If not, how can I make PulseAudio work properly?

---

### Post by TheLions on 2009-03-19
you can try installing newer version of pulseaudio and alsa from jaunty (be sure to know what are you doing...)

---

### Post by Peasantoid on 2009-03-19
What is this "jauntry" of which you speak?

---

### Post by TheLions on 2009-03-19
> **Peasantoid said:**
> What is this "jaunty" of which you speak?

its alpha of 9.04 version of Ubuntu
you can take a peek:[http://ubuntuforums.org/forumdisplay.php?f=352](http://ubuntuforums.org/forumdisplay.php?f=352)

---

### Post by acimmarusti on 2009-03-19
The gnome package for bluetooth that Ubuntu 8.10 uses is known to be broken, especially using skype. People have fixed the problem by using the newer packages for bluez-gnome and pulseaudio that Jaunty uses (Ubuntu 9.04 - testing phase). You can find them using the jaunty repository. But be careful!

Take a look at this bug report, especially the last posts: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/285412](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/285412)

---

### Post by Peasantoid on 2009-03-19
Oh, Jaunty, right. *facepalm*

I'm kind of a newbie when it comes to this sort of thing, so could you give me a walkthrough on how to install the aforementioned packages, if it isn't too much trouble?

[edit] Edited for politeness. :)

---

### Post by Peasantoid on 2009-03-19
I morally object to bumping, but...could really use a response here...

---

### Post by acimmarusti on 2009-03-19
ok, here is what you should do:

Open System > Administration > Synaptics > Settings > Repositories > Third-Party Software > Add

In the box paste and copy this:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main restricted universe multiverse

Then click close and reload. Once it fully reloaded go to the search box and type bluez. Right click on the package bluez to upgrade it and accept the dependencies. Then search pulseaudio and upgrade that package too.

Install those packages and then go back to third-party repositories and disable the one you just added and reload synaptics again.

Hopefully this will work fine. But I warn you, that I've never done this myself. I know how to do it, and other people claim that it has worked for them, but do it at your own risk.

---

### Post by hikaricore on 2009-03-19
Title edited...

---

### Post by Nano_ext3 on 2009-03-19
You may want to go to your settings and to the "Sound" manager in Ubuntu (System > Preferences > Sound). The ALSA driver is known to work on many occasions where the real driver fails to work. This happened to me on my desktop, which is understandable as it is choc full of custom hardware. Change each entry on the main page of the sound editor to ALSA. You can test the output by hitting the test button. Change your driver if ALSA does not work, one of the drivers in each drop down should work, but you want to keep the same driver for all if you can.

Also install alsamixer as suggested above, it will greatly help you out. Turn all levels up from alsa mixer. The command to istall alsamixer is:

"sudo apt-get install gnome-alsamixer"


Cheers!

---

### Post by Peasantoid on 2009-03-19
I installed the Jaunty PulseAudio (and seem to have inadvertently borked it; it gives me crap about not being part of pulse-rt. Not like I particularly wanted it anyway). Then I switched all the drivers to ALSA, like Nano said. Yeah, it made my sound work, but &#8212; and this is the critical part &#8212; it did not make it come out of my headset. Which is why I was diddling around with PA in the first place, because apparently it's the only one that supports redirection.

I can still directly specify the device with programs such as mplayer, but not so with system sound. So now I'm kinda looking for PulseAudio *alternatives*. You know, ones that can redirect.

Anyway, thanks to everyone who helped me. Still open to advice though. :)

---

### Post by TheLions on 2009-03-20
> **Peasantoid said:**
> I installed the Jaunty PulseAudio (and seem to have inadvertently borked it; it gives me crap about not being part of pulse-rt. Not like I particularly wanted it anyway). Then I switched all the drivers to ALSA, like Nano said. Yeah, it made my sound work, but — and this is the critical part — it did not make it come out of my headset. Which is why I was diddling around with PA in the first place, because apparently it's the only one that supports redirection.

I can still directly specify the device with programs such as mplayer, but not so with system sound. So now I'm kinda looking for PulseAudio *alternatives*. You know, ones that can redirect.

Anyway, thanks to everyone who helped me. Still open to advice though. :)

maybe new alsa can help...
[http://www.alsa-project.org/main/index.php/Download](http://www.alsa-project.org/main/index.php/Download)
[ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.19.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.19.tar.bz2)

look at file named INSTALL for instruction how to complie it

---

### Post by Peasantoid on 2009-03-20
Okay, turns out I borked Bluetooth as well. Fortunately, I had a pre-borkage system backup on hand and got everything working properly once more.

The moral of the story? Don't install stuff unless you *really* know what you're doing.

Ahh, thanks for the tip about the new ALSA. May get around to installing that, once I know it won't break anything important. :)

---

