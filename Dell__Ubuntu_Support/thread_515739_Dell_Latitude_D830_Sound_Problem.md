---
title: "Dell Latitude D830 Sound Problem"
date: 2007-08-02
forum: Dell  Ubuntu Support
---

### Post by rmullins on 2007-08-02
Ok, I have been trouble-shooting this laptop for awhile now.  Just being able to install Ubuntu on this thing has been rough.  IO errors for screens, getting dumped in busy box during installation, incorrect Intel 3100 drivers, etc, etc.

Now, I cannot seem to get the sound up and running.  Anybody have any thoughts on this.  I've futzed around with the preferences, and read through about a dozen or more threads on enabling AlSA, making sure I'm not muted, etc, etc and I still cannot seem to get things going.

Is anyone else having this difficulty with the D830 and sound?  Any help would be appreciated.

Thanks.

---

### Post by rmullins on 2007-08-02
Update:

Went to the Ubuntu help on IRC.  Was pointed in this direction.
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

I followed the directions and rebooted the first time.  Now my sound card isn't detected at all.  I ran lspci and got this report on my sound card.
*Audio device: Intel Coporation 82801H (ICH8 Family) HD Audio Controller*

Instructions at the above website said that if I still didnt have sound then I needed to edit my alsa-base configuration file by adding the line;
*options snd-hda-intel model=3stack* and replace 3stack with my model which can be found in ALSA-Configuration.txt file.  I am loking in there under the module for Intel HD audio, but I cannot seem to find my model name.  Can someone help me with this?

---

### Post by fred168 on 2007-08-02
I know this may not be helpful, but I've had no trouble with sound on the D830, (except I lose sound after a suspend). For the install I basically followed "susan_1890"'s second post (concerning the D630) [[here]]("http://ubuntuforums.org/showthread.php?t=481651")

then did the workaround to get cd to work 
[[here]]("http://ubuntuforums.org/showthread.php?t=477516")
(see voland666 there)

and then updated the intel driver (for sharper screen):
[[here]]("http://ubuntuforums.org/showthread.php?t=494943")

Most things seems to work fine (wifi, sound, suspend [minus sound], dvd,...not tested bluetooth yet, Beryl causes a crash)

---

### Post by cnshzj007 on 2007-08-02
> **rmullins said:**
> Update:

Went to the Ubuntu help on IRC.  Was pointed in this direction.
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

I followed the directions and rebooted the first time.  Now my sound card isn't detected at all.  I ran lspci and got this report on my sound card.
*Audio device: Intel Coporation 82801H (ICH8 Family) HD Audio Controller*

Instructions at the above website said that if I still didnt have sound then I needed to edit my alsa-base configuration file by adding the line;
*options snd-hda-intel model=3stack* and replace 3stack with my model which can be found in ALSA-Configuration.txt file.  I am loking in there under the module for Intel HD audio, but I cannot seem to find my model name.  Can someone help me with this?


I make sure that the latest driver of the sound card has no name about D630 and D830.

---

### Post by Yorthegreat on 2007-08-06
<shameless plug>
I've been trying to put together a howto. I'm using feisty myself and got basically everything working. Gutsy in its current state is a nightmare.

Feedback appreciated:
[kubuntu-on-dell-latitude-d830-with-intel-gpu]("http://www.jordswart.org/kubuntu-on-dell-latitude-d830-with-intel-gpu")
</shameless plug>

---

### Post by cacycleworks on 2007-08-11
oh wow, i'm going to sound like a broken record... I just posted this to another thread. The D630 and 830 are quite similar (looks like the screen size is only diff), so maybe these would help someone:

----------------------
Did you see my install guide? Few steps, no compiling, and everything is working on my D630 "out of box" from 64bit kubuntu alt cd.

[http://ubuntuforums.org/showthread.php?t=518702](http://ubuntuforums.org/showthread.php?t=518702)

Here are some of my thoughts about the ICH8...
[http://ubuntuforums.org/showthread.php?t=521751](http://ubuntuforums.org/showthread.php?t=521751)
---------------------

This should work on D830, if not please let me know!! :D 

Also, there is an ipw4965 thread in the case you have that (and not my ipw3945, which is supported by the kernel) :
[http://ubuntuforums.org/showthread.php?t=493095](http://ubuntuforums.org/showthread.php?t=493095)

---

