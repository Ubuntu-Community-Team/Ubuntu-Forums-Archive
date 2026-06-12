---
title: "MPlayer playing single realaudio stream multiple times simultaneously"
date: 2006-09-25
forum: Desktop Environments
---

### Post by leapy on 2006-09-25
Hello

Following a previous issue trying to get sound working in Firefox/flash player in Edubuntu 6.06.1 (Dapper Drake), I followed instructions available at
[http://www.mail-archive.com/edubuntu-users@lists.ubuntu.com/msg00230.html](http://www.mail-archive.com/edubuntu-users@lists.ubuntu.com/msg00230.html)
and
[http://www.macewan.org/2006/06/01/howto-firefox-flash-video-sound-on-ubuntu-linux-dapper/](http://www.macewan.org/2006/06/01/howto-firefox-flash-video-sound-on-ubuntu-linux-dapper/)

I now successfully have sound when viewing flash presentations and games in Firefox. However, when I click on an realaudio link within Firefox, MPlayer fires up and plays the stream three times simultaneously with slightly different start points. What a racket! 

Opening a local mp3 file works correctly - only one instance is heard.

I assume that I have fiddled a bit too much. Where should I start looking for a solution? Is it possible to limit MPlayer to one instance at a time?

Many thanks for assistance.

Leapy

---

### Post by gatti on 2006-09-25
Sorry not much help but the same thing happens when I open a streaming video link in FF. I did the install from automatix and it worked straight away. Posted the prob on this forum a few weeks ago but nobody replied

---

### Post by leapy on 2006-09-26
Hi Gatti

Thanks for your note. What do you mean when you say "I did the install from automatix and it worked straight away." - you mean it worked correctly at first and then broke or it has always tried to play multiple copies? 

It is interesting that this happens for you with video - mine is fine for video - just audio realaudio streams.

Would it help if I posted my mplayer and mozilla conf files for you to compare?

L

---

### Post by gatti on 2006-09-26
Your original post quoted two links so I assumed that you had some hassle getting it working. I installed from automatix and it worked with both audio and video straight away. Unfortunately the three times start fault was also present from the start and no amount of fiddling cured it. I stuck with mplayer because of the range of media types supported.

Now the good news, I completely uninstalled mplayer last night and re-installed the latest ver from automatix and it now works perfectly - only one instance starts when I click a link.

---

### Post by leapy on 2006-09-26
Gatti

Thanks for getting back again, I appreciate the effort. 

I will try and copy you and see how I get on.

L

---

### Post by leapy on 2006-10-05
Hi Gatti

Well, that worked!

Many thanks, everything works correctly.

For the sake of google: 

a) Uninstall anything you have already related to flash, mplayer.

b) download automatix from:
[http://www.getautomatix.com/](http://www.getautomatix.com/)

c) Install automatix

d) run it and install flash and mplayer plugins from automatix

L

---

