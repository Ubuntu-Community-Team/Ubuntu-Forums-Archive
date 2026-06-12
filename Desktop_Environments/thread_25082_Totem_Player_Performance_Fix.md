---
title: "Totem Player Performance Fix"
date: 2005-04-09
forum: Desktop Environments
---

### Post by mksmith on 2005-04-09
I have read a couple of issues about the Totem player playback and have experienced them myself.

I have found that by completing the following I was able to get smooth playback.

* Follow the steps outlined at Unofficial Ubuntu 5.04 Starter Guide [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/) and:

1) install the multimedia and w32 codecs
2) install the libdvdcss2 library
3) install the totem-xine library - $ sudo apt-get install totem-xine
4) ensure your video card is correctly configured
5) change the DMA settings for your dvd player - $ sudo hdparm -d 1 /dev/dvd
6) reboot

I'm only new to Linux so most of you should be able to follow - I think the main issue was probably not having DMA turned on.

The player now works great!  Hope this helps others.  \\:D/ 


Regards,

Matt

---

### Post by fsman on 2005-04-09
Hum

Sound's like an admission of defeat that Gstreamer doesn't really work and therefore  people need to use xine.

Anyone got good performance from Gstreamer?

---

### Post by mksmith on 2005-04-09
Yeh it doesn't seem to be quite up to the same standards.

Another quick one - how do I make the DMA change permenant?

---

### Post by ciocanel on 2005-04-09
[QUOTE=mksmith]
Another quick one - how do I make the DMA change permenant?[/QUOTE]

Try editing /etc/hdparm.conf .

---

### Post by mksmith on 2005-04-09
Thanks for your help!

---

### Post by vaskark on 2005-04-09
I tried all of the above tips, but dvd playback is still choppy for me. DVDs play a little smoother for me in MPlayer, but still not 100% (like I get on my Win partition).
Sigh.

---

