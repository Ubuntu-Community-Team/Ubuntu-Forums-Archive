---
title: "Enemy Territory sound woes ... redux"
date: 2006-03-31
forum: Gaming &amp; Leisure
---

### Post by teshue on 2006-03-31
Hello there folks, I've got a problem that has been driving me insane.

I got a new soundcard a few weeks ago, Soundblaster Live! 24-bit. Needless to say, getting that to work was a pain in the butt, but I eventually got it working. Everything soundwise works on my computer except for Enemy Territory and its mods. I can listen to music while playing ET, but even if I have my music program closed the sound still does not work. It is as if it is muted.

Here is what I get when I run ET in a console:

------- sound initialization -------
------------------------------------
----- Sound Info -----
sound system is muted
    1 stereo
32768 samples
   16 samplebits
    1 submission_chunk
22050 speed
0x0xaedcf000 dma buffer
No background file.

My current new card is _card1_, as opposed to card0. My gstreamer properties are set to esd for output and oss for input.

Thanks.

---

### Post by Zimmer on 2006-03-31
[http://ubuntuforums.org/showthread.php?t=98167](http://ubuntuforums.org/showthread.php?t=98167)
post #6 may help...
..and post #14
[http://ubuntuforums.org/showthread.php?t=80926&page=2](http://ubuntuforums.org/showthread.php?t=80926&page=2)
works for me and
seemed to work for Buddy...
I have now encapsulated the commands in a script...

---

### Post by teshue on 2006-03-31
Nope, neither worked.

Thanks for the reply though.

---

