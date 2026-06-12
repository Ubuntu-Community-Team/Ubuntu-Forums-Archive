---
title: "Sound Glitches"
date: 2009-06-18
forum: General Help
---

### Post by zeug on 2009-06-18
I have noticed that recently when the system plays sounds like the notification sounds in Pidgin (contact log in/out etc.), the sounds makes there weird clicking-buzzing sound.  This happens in both the headphones and on the speakers, and it happens irregularly.  Right now it has mostly been the left side of the headphones and the speakers that do this but the right side has done it before a few times.

What is the cause of the clicking? Is there a way to fix it?

[Laptop, XPS1530.]

zeug.

---

### Post by zeug on 2009-06-19
Bump. It is kind of getting annoying because now it happens more frequently (still with the Pidgin notification sounds).

Any ideas?

zeug.

---

### Post by h_ryan503 on 2009-06-19
I have the same problem on my system. It seems to only happen however when I'm using the Pidgin-Encryption plugin.

---

### Post by zeug on 2009-06-20
I just checked, I do not have that plugin installed.  Also, it happened for a bit while watching a movie, too.

zeug.

---

### Post by Strongman332 on 2009-06-20
i have the same problem on the same computer

---

### Post by zeug on 2009-06-24
Bump.
No one?

zeug.

---

### Post by rainwalker on 2009-07-09
Same problem on my Thinkpad W700. This is the only thing Google tells me:
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1535991.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1535991.html)
> 
[Bug 342946] Re: intermitten buzzing from speakers using hda-intel alsa on dell mini 9 jaunty netbook remix

supercompman
Sun, 14 Jun 2009 21:35:33 -0700

I also have problems with Pidgin's notifications causing buzzing sounds
on both my Eee PC 900HA and on my desktop machine (I'm just using the
on-board sound of the MSI K9A2 CF-F motherboard). A quick workaround
I've used for both machines is to install alsaplayer with the text
interface and set the sound method in Pidgin to "Command" and use this
command to play the sound:

alsaplayer -i text %s

Using that, everything sounds fine... no more buzzing sounds. It's just
disappointing that this doesn't work correctly right out of the box.

PulseAudio is finally working perfectly for me, so I'm wary of messing with sound at all. Can anyone verify that this works?

---

### Post by xenogia on 2009-07-09
Another idea would be to uninstall PulseAudio and just use Alsa, I also upgraded the alsa revision to 1.1.20 I think it is.  And everything is working great now :)

---

