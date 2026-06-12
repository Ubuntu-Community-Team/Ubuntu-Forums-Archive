---
title: "love ubuntu - hate the lockups!"
date: 2005-10-11
forum: Desktop Environments
---

### Post by rockatship on 2005-10-11
hi there,

I've been using Ubuntu 5.04 for about a month now, and I love it. Probably my favourite linux build to date (not that I'm a big linux expert anyway).

My only issue (which is becoming more and more annoying) is that there seems to be some kind of memory leak happening somewhere that will cause my system to lock up to the point of a necessary hard reset.

The lock ups happen variably. I noticed them happening a lot using Java programs (Azureus, JAlbum, etc.) in that once a few other programs were open with Firefox the system would crash. I also get it if I load more than 3 or 4 photos in Gimp, and just now I've realized I can't get through about 15 minutes of a video in MPlayer (with nothing else open after a fresh restart) without a lock-up.

Under general use however (firefox, terminals, etc.), things can work fine with the machine left on for days (so I don't think it's has anything to do with Gnome itself). But if I start to load things up just a little bit heavier with Azureus and what not, I'm headed for a lockup.

Now I'm working off a P3-1000, 256 MB ram, which I know isn't a heck of a lot, but you'd expect I should be able to run a movie for a few minutes or keep azureus open while browsing the internet for a few hours.

Any ideas? Does Ubuntu have any sort of virtual memory concept that I could expand, or something similar?

Thanks

Dan

---

### Post by Emerzen on 2005-10-12
Some programs are known to have memory leaks...I believe Azureus may have been one of them, in the past, but it should be fixed now.

Anyway, virtual memory in linux is known as your swap partition.  If you do a search in these forums under "swap" I'm sure you'll turn up lots of info.

---

### Post by pmj on 2005-10-12
It might be that you have bad RAM or that the CPU is overheating. Both of these have caused several complete lock-ups for me until I got them fixed. For the CPU, it was as easy as removing 2 years' worth of dust from the heatsink and fan. :)

---

