---
title: "New Twist on an Old Problem: Wine sound delay"
date: 2007-03-20
forum: Gaming &amp; Leisure
---

### Post by EvilMarshmallow on 2007-03-20
I've been reading old posts enough to know that alsa drivers in wine may cause a delay for your sound.  I've also learned that using OSS should fix it.  However, I've got a little issue:

When I switch my winecfg to OSS, I get a message upon starting my game (Call of Duty) that says "166 sound files missing or in a bad format".  I assume this means that I'm missing part of the OSS package.  What should I install?  I looked for "OSS" in the repos and I already had the only package I could find.

---

### Post by willskills on 2007-03-20
I think anywhere you read, people warn away from alsa & wine. Use OSS :)

Wine does spit errors when you try to select OSS (but it's usually libjack errors) - not what you have posted. So I am stumped! Sorry I can't be any further help.

---

### Post by EvilMarshmallow on 2007-03-20
Does hardware make a difference?  Mine is onboard audio rather than a PCI card.

I did encounter libjack errors (or something like that) and I found the JACK driver packages and installed them.  I've tried every combo on the audio page in winecfg though and nothing's worked.

---

### Post by leilei on 2007-03-20
I get worse in Call of Duty on wine too. It's just unplayably slow (less than 1fps) in complex sound areas. I dunno why this game is marked gold on winehq if this is quite a severe problem

---

