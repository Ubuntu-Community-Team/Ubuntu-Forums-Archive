---
title: "Inspiron 1501 display drivers breaking"
date: 2008-10-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Spazztastic on 2008-10-15
Greetings!

I've bolded the parts for those of you who don't want the backstory :)

Recently I decided to switch over to Ubuntu because I no longer have to travel much with my laptop and I use it only for things your typical user would. As I understand special drivers have come out for my model of laptop in the past year (It's been that long since I used it last) and I wanted to give it a shot.

[b]I'm using an Inspiron 1501, 2048MB RAM (Non-stock), AMD Turion processor, and a Radeon x1150 video card. When I do a fresh install of Ubuntu, it asks me to apply the special video drivers right off the bat. Typically I do that, restart, and everything works fine. It performs well at the 1280x800 resolution.

However, once I apply the following:```
sudo apt-get update && sudo apt-get dist-upgrade
```Then I restart as it requests, my video drivers become undetectable. Am I doing something wrong here? [/b]

Right now I'm in the process of re-installing once again, I've set up different partitions home, var, boot, etc. so I can provide logs if this one craps out too. This time I'm going to apply the dist-upgrade first, then apply the video drivers. If this fixes it, I'll close this thread.

Any suggestions are helpful.

---

### Post by Spazztastic on 2008-10-15
Yep, even after doing the update AFTER the dist-upgrade it breaks.

Any suggestions?

---

