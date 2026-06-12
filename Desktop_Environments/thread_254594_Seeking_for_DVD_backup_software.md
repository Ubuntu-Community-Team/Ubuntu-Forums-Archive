---
title: "Seeking for DVD backup software"
date: 2006-09-10
forum: Desktop Environments
---

### Post by qrwe on 2006-09-10
Hello,

I'm sitting here with my own DVD that I want backup on. As I prefer quality over speed, I used HC Encoder 0.18 instead of DVD Shrink back in my Windows days = *much *better output. Here in Ubuntu, I think I'll have to start all over in my DVD backup process knowledge.

I seek suggestions in:
**1) **What program should I use to rip of the actual movie (not menus and all other fancy extras) from my DVD?
**2) **Any good programs to transcode AC3-audio -> any other format, even AC3 again.
**3) **Most important :): a program that converts the movie files into a DVD-complient output with as good quality as possible.
**4) **A program to make the previous mentioned output into DVD-files for burning (a GUI for making my own menus would be preferrable :)).
Big thanks for any help!

PS. If there's a good Linux DVD-ripping guide out there somewhere, be my guest! :) DS.

---

### Post by tuxinvader on 2006-09-10
You should check out dvd::rip. I'm not sure what repository it is in. It's a perl GTK+ GUI frontend to transcode and other tools. I think it will do everything you want.

sudo apt-get install dvdrip

---

### Post by qrwe on 2006-09-10
Actually, I've tested dvd::rip. Even if it's worth mentioning for it's smart and simple interface, it only supports making of MPEG-4 video (like XviD, etc.) or if I want to make SVCD:s or similar. It can't handle >= 2-pass for any MPEG-2 encoding either. At third, it was only fully functional in sudo mode (it couldn't access necessary libs otherwise).
But thanks anyway ;) Any other suggestions, anyone?

---

### Post by lukew on 2006-09-10
Hi,

I could not get dvdrip to work, nor k9copy.

I use dvd decrypter and dvd shrink through wine. Works excellently!!!

Luke

---

### Post by lukew on 2006-09-10
BTW,

I used a combination of the two; the tope one refers to an application which I could not find.

[http://mrbass.org/linux/ubuntu/dvdshrink/](http://mrbass.org/linux/ubuntu/dvdshrink/)
[http://www.ubuntuforums.org/showthread.php?t=78611&highlight=wine](http://www.ubuntuforums.org/showthread.php?t=78611&highlight=wine)

Luke

---

### Post by lukew on 2006-09-10
Oh,

And to make dvds from smallers files, like avis and mpgs etc, I used these:

[http://tovid.wikia.com/wiki/Todisc](http://tovid.wikia.com/wiki/Todisc)
[http://ubuntuforums.org/showthread.php?t=183936](http://ubuntuforums.org/showthread.php?t=183936)
[http://smorgasbord.net/convert_video_linux](http://smorgasbord.net/convert_video_linux)


Luke

---

### Post by qrwe on 2006-09-10
And I still do not want DVD Shrink ;) Plus, I've never got wine to work so very well for me, but I don't care about it on the other hand - except this topic I have what I need in Ubuntu.
(OK, there are some games though..)
Does anyone have any experience with [ffmpeg]("http://ffmpeg.mplayerhq.hu/index.html") in Linux? Quality, speed, MPEG-2, DVD-compliance, anything?

---

### Post by themunkee on 2006-11-07
I'm using Edgy on a 64 machine and was having issues with Wine to get DVD Shrink working. I like backing up my DVDs with subtitles and menus onto my hard drive (although there is options not to). I've found that k9copy seems to work a treat, however it takes about 5-10mins longer than DVD Shrink did with XP. I've also managed to rip DVDs to ISO fine. k9copy also appears to have options to rip to XVid and MPEG.

---

