---
title: "Wine problem"
date: 2007-03-12
forum: Gaming &amp; Leisure
---

### Post by Kilrain on 2007-03-12
After hearing so many good things about Cave Story I decided to download Wine and give it a playthrough.  At first I got no sound or video, but I was able to fix the sound problem in winecfg by switching the driver to alsa, but I'm still getting a black screen.  I've heard Cave Story has problems in windowed mode but fullscreen is a no-go as well.  Any ideas as to where the problem might be?  Thanks a lot.

EDIT: also, upon starting wine or winecfg through the terminal I get this error message: "libGL warning: 3D driver claims to not support visual 0x4b"  I hope this isn't a hardware issue...

---

### Post by conjur3r on 2007-03-12
What type of video card do you have?  Have you got the drivers installed?

Is it a freely available game?  If so, let me know and I'll give it a try on my end.  I'm running an nvidia card using the latest wine 0.9.32 version.

---

### Post by Iarwain ben-adar on 2007-03-12
nvm.. (didn't read the post completely)

This is the download link
[clicky](http://www.acid-play.com/download/cave-story/)


Iarwain

---

### Post by Lystrodom on 2007-03-12
I can't help you, but wanted to say good luck. Cave Story is excellent.

---

### Post by Kilrain on 2007-03-12
@ conjur3r: Not exactly sure what video card / drivers I'm running.  I'm on a slightly old laptop, so nothing fancy or meant for gaming, but I've run stuff like WoW (yeah, I'm not proud of it) which I'd assume is more taxing on the system than Cave Story.  'Course, back then I was still running Windows.  How would I check which video card I have in ubuntu?

---

### Post by conjur3r on 2007-03-12
I'll give it a go when I come back from work.

This page seems to suggest that it works fine under wine: [http://72.14.235.104/search?q=cache:V4pvm3HmCr8J:danieldematteis.wordpress.com/2006/03/28/cave-story-on-psp-imminent/+cave+story+linux&hl=en&ct=clnk&cd=1&gl=au&client=firefox-a](http://72.14.235.104/search?q=cache:V4pvm3HmCr8J:danieldematteis.wordpress.com/2006/03/28/cave-story-on-psp-imminent/+cave+story+linux&hl=en&ct=clnk&cd=1&gl=au&client=firefox-a)

---

### Post by conjur3r on 2007-03-13
I've had a crack at it and I'm getting what you are: sound but no video.  I've tried using cedega and it works ok there.

What version of wine are you using?  It may be the wine version that is causing the problem.  The wine db seems to suggest more successes than not: [http://appdb.winehq.org/appview.php?iVersionId=4851](http://appdb.winehq.org/appview.php?iVersionId=4851)

---

### Post by Iarwain ben-adar on 2007-03-13
Well,
to be honest:
it works like a charm on my pc (Feisty with wine 0.9.32)


Iarwain

---

### Post by Kilrain on 2007-03-13
Running Wine 0.9.30, tried installing cvscedega after reading of your success with it but couldn't figure it out.

Anyway, I found a fix to my problem after playing around with some settings in winecfg.  Checking "emulate a virtual desktop" seems to set everything straight.

---

### Post by conjur3r on 2007-03-13
That's sweet!  I tried that option but it hasn't worked.  No biggy, glad you got it sorted!

---

