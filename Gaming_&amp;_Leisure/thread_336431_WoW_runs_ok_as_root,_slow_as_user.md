---
title: "WoW runs ok as root, slow as user?"
date: 2007-01-11
forum: Gaming &amp; Leisure
---

### Post by SuperEe on 2007-01-11
Ok so I got world of warcraft running ok using wine. I copied the wow directory from an ntfs partition onto a reiserfs partition and changed all the permissions to my user with 

```

sudo chown username /wow -R
chmod u+wrx /wow -R

```

But my fps was horrible. So after trying a bunch of different things I switched to root with su root and ran wow and the fps was about double, running fine. I also tried running with sudo, but then the fps was bad again. I'm guessing my user doesn't have some other permissions here, what would those be? Or does this have to be with less processes running with root or what?

I'm using xubuntu edgy 6.10 with an nvidia graphics card.

Any help would be nice, I'm fairly new to linux but I do realize I don't want to be running WoW as root each time..

---

### Post by Ferrat on 2007-01-11
This is just a guess but two things

1. when you run as ROOT do you have the same amount/programs running?

2. have you tried using nice -20? (upping the prio of WoW)

---

### Post by SuperEe on 2007-01-11
Sure enough, it was the process load. nice -20 didn't help so created a new user and now it's working great.

Ty for the help :)

---

### Post by Ferrat on 2007-01-12
np =)

---

