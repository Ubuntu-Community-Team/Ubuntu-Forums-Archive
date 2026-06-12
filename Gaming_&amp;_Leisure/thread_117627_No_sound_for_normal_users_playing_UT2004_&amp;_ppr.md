---
title: "No sound for normal users playing UT2004 &amp; ppracer"
date: 2006-01-15
forum: Gaming &amp; Leisure
---

### Post by edistar on 2006-01-15
Hey!
My sound didn't work with UT2004 & ppracer. Then once i by accident started ut as root and I had sound.
Why do restricted users not have sound in UT or ppracer?
Seems strange to me, how can I 'correct' this problem?

Regards,
Edwin

---

### Post by GeneralZod on 2006-01-15
Newly created users are granted very few priviledges by default.  You'll need to add them to (I think) the "audio" group.  There's probably a GUI for it somewhere, but I don't use GNOME so I can't really help you with that. 

Good luck!

Edit:

Wait - I misread your post.  Ordinary users should have sound out-of-the-box (I did), and I'm not sure why you haven't.  Make sure your "restricted" users is in the audio group, and make sure you have "write" permission to /dev/dsp.

---

