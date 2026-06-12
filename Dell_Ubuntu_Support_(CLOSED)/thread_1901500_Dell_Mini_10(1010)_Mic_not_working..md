---
title: "Dell Mini 10(1010) Mic not working."
date: 2011-12-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by JWColeman on 2011-12-28
I've fiddled with alsamixer for probably an hour or so now.  I've gotten my sound to work just fine.  I have the alc269.

I changed the alsa-base.conf file to contain this bit of instructions:

alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=basic

I got this info off of a wiki - [http://en.gentoo-wiki.com/wiki/Dell_Inspiron_Mini_10_(1010)#Audio](http://en.gentoo-wiki.com/wiki/Dell_Inspiron_Mini_10_(1010)#Audio)

I've been playing with sound settings for a while now and I'm pretty taxed, has anyone gotten a mic to work on a dell mini 10(1010) ?

---

### Post by JWColeman on 2011-12-28
I've tried the toshiba model now too, that doesn't work.

Alsamixer doesn't have my specific model unfortunately.

---

