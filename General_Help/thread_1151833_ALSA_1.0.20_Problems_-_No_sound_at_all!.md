---
title: "ALSA 1.0.20 Problems - No sound at all!"
date: 2009-05-07
forum: General Help
---

### Post by tyrion2323 on 2009-05-07
Hi everyone,

Well, I'm currently working on the following platform:
Ubuntu 9.04 (Jaunty)
Intel DG45FC ITX Motherboard

**Situation**
This motherboard has an HDMI output on it; however, reports have been that the HDMI does not properly transmit audio.  Several people claim that the 9.04 kernel + ALSA 1.0.19 drivers fixed this.

So I downloaded the recent ALSA drivers (1.0.20) and followed the installation instructions:
[LIST]
[*]I ran ./configure
[*]I ran make
[*]I ran sudo make install
[*]I ran ./snddevices
[/LIST]

Unfortunately, when attempting to gedit /etc/modprobe.conf, I found out that there doesn't seem to be a modprobe.conf.

Because of this, I was unable to continue.

**The problem**
Well, the problem is quite simple - Now I've got no audio!

Now, clearly this is my fault...but I'm simply not knowledgeable enough to know how to fix this.

Can anyone help me out?

Thank you :)

---

