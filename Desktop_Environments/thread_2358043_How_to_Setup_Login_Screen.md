---
title: "How to Setup Login Screen"
date: 2017-04-09
forum: Desktop Environments
---

### Post by webmiester on 2017-04-09
Hi Everyone,

I am using Ubuntu Mate on a raspberry pi.  After bootup, I am greeted by a boring login screen with a white background and a box which displays my first user's name as default.

I would like to change the background and make the "guess" user as the default name which will appear.  How do I do this?

Thanks so much.

---

### Post by TheFu on 2017-04-09
Create a userid - "guess" - then login using that account.  It should be the default account shown going forward.

If you meant the "guest" login - those are randomly generated userids (guest4352 for example) with each new time they are requested. It is created when requested and removed when logout happens.

**lightdm** is the login/display manager for mate, if you want to know more. Config files for it are in /etc/lightdm/ with many different options.
[https://wiki.ubuntu.com/LightDM](https://wiki.ubuntu.com/LightDM) and [https://www.freedesktop.org/wiki/Software/LightDM/](https://www.freedesktop.org/wiki/Software/LightDM/) have more info.

---

### Post by webmiester on 2017-04-20
Thanks so much!

---

