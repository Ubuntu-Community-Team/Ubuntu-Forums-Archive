---
title: "Problem: Sound-juicer won't rip!"
date: 2005-04-13
forum: Desktop Environments
---

### Post by madzzoni on 2005-04-13
The standard CD-ripper in Hoary, **sound-juicer** won't rip CD's as .waw format, or mp3, it's just start up an then do nothing else but create the folder!
It will only rip as .ogg/.flac.

I got lame and liblame installed.

Now i using **Grip**, which is working as it supposed to do... ripping CD's, but not as nicely integrated in the desktop, as Sound-juicer!

What is wrong with Sound-juicer? It's too bad the default app's dosn't do the right job, especially for all the new users of my favorite Linux-desktop, Ubuntu 5.04.

(BTW, sound-juicer worked perfect in Warty.)

---

### Post by Stormy Eyes on 2005-04-13
If I remember right, Sound-Juicer uses the GStreamer multimedia framework. According to [this FAQ](http://www.ubuntulinux.org/support/documentation/faq/helpcenterfaq.2004-09-16.3469703387), if you want MP3 support you have to start by adding the *universe* repository and running **sudo apt-get install gstreamer0.8-mad**. Hope this helps; I stick with Ogg when ripping CDs, so I can't make promises.

---

### Post by madzzoni on 2005-04-13
I got the gstreamer08-mad installed for mp3, but i want to rip CDs as .wav

This was possible in Warty.

---

