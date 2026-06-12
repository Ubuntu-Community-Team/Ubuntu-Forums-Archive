---
title: "RuneScape HD on Ubuntu 64-bit"
date: 2009-11-23
forum: Gaming &amp; Leisure
---

### Post by Frogging101 on 2009-11-23
I want to be able to run RuneScape HD on 64 bit Ubuntu. But, if I just use sun java, I can't play my music at the same time as RuneScape because of ALSA/pulse issues. IcedTea works for this, but HD doesn't work. It just says 'Unable to enter this display mode' when I click HD. What should I do?

---

### Post by dagoth_pie on 2009-11-24
install the "alsa-oss" package, then run in your terminal type```
aoss firefox
``` and it will let you play your music at the same time, after you've confirmed that works right click your applications menu then add aoss in front of firefox in the command under the firefox shortcut. From then on you shouldn't have any problems.

---

### Post by Frogging101 on 2009-11-24
That doesn't work. As soon as RuneScape starts loading, the music stops. I am using 32-bit firefox, and 32-bit sun java (But I have 64 bit ubuntu), which I need to do in order to run RuneScape in HD mode. I use pulseaudio. I tried padsp, but that doesn't do anything.

---

### Post by dagoth_pie on 2009-11-24
bizzare, how does the music stop play, does it seem like it's still trying to play just with no sound comming out, does it just stop and give an error, or something sifferent?

---

### Post by Triggerhapp on 2009-11-24
Makoto on RS forums confirmed theres some kinda bug in padsp which stops its use for RS/Firefox. I personally make do without sound. I hate the sound

About HD and 64bit, it's currently not possible, A few people now have sent a bug report to Jagex about it, hoping they move on it.

---

### Post by Frogging101 on 2009-11-24
The music simply stops playing. No error message (using rhythmbox), and it shows that it is still playing. It won't play again unless I restart alsa/pusleaudio. And RSHD on Ubuntu 64-bit IS possible, I managed it last night with icedtea. The sound also worked properly with icedtea! But in the morning, it broke.

---

### Post by Potted Meat on 2009-11-29
I also play RS and since upgrading to Karmic can not play RS with Firefox and use any other sound apps.  In Jaunty and before I could simply use padsp but that no longer works.

Ever since I switched to Ubuntu three years ago, I've been fighting with sound issues.  I've just about had enough of it.

Sound is huge problem in Linux and there is absolutely no excuse for it being so complicated and troublesome.  I switched to Linux so I wouldn't have to waste so much time dealing with malware, virus, etc but now it's coming to the point where I'm spending more time dealing with sound issues in Linux than I would be dealing with ALL issues in Windows.

---

