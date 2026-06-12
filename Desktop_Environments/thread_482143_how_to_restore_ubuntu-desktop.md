---
title: "how to restore ubuntu-desktop"
date: 2007-06-23
forum: Desktop Environments
---

### Post by ubukool on 2007-06-23
Hi friends,

In installing compiz-fusion earlier on today, I managed to accidently uninstall ubuntu-desktop.  Now when I boot up I get the login screen and upon inserting my username and password, there is a brief flurry of activity as the ubuntu splash screen comes up, and then I am left staring at the orange screen of death with a single cursor on it.   It won't do anything else!#-o

I read on this forum that someone else had a similar problem and solved it by reinstalling ubuntu-desktop with:

sudo apt-get install ubuntu-desktop

When I try to do this, it looks promising and then it tells me that the respository is unresolved and that it was unable to fetch the file.   Is this because there is no internet connection?

So now I'm stuck.  Does anyone have any ideas how I can connect to the internet and reinstall ubuntu-desktop?  Any help would be very gratefully received! :)

---

### Post by Kobalt on 2007-06-23
I think the reason of your breakage isn't the ubuntu-desktop package, rather your compiz installation. What you should do is remove your compiz packages and then try to boot up, so that you can get back your internet connection (I suppose you have a wifi connection and that you use Network-Manager, otherwise you should be able to connect before your session starts).

---

### Post by ubukool on 2007-06-23
Hi Kobalt,

Thanks for coming to the rescue!   I'll do as you suggest and let you know what happens.

;)

---

### Post by ubukool on 2007-06-23
Hi Kobalt,

Thanks for the advice, I removed all the compiz packages and I was able to boot into gnome again! :D

The funny thing is, there's SOME kind of compositing window manager working even though I've removed compiz and it looks like it's still compiz-fusion.  I don't know how that can be!

Do you have any advice for installing and using compiz-fusion?  I didn't think it would break my system, can I stop it from happening again?

Thanks for all your help ;)

---

### Post by raul_ on 2007-06-23
Take a look at the sticky in the Desktop Customization section. 

and make sure you don't remove anything important :D

---

### Post by Kobalt on 2007-06-23
I haven't been into testing the new version of Compiz yet so I can't really give you advices on that...

---

### Post by ubukool on 2007-06-24
Kobalt and Raul,

Thanks for your help, it's a great relief to have my system back together in one piece.  Beryl is looking particularly sweet at the moment :D   I guess this is a great lesson in being satisfied with what you've got.  If it ain't broke, don't fix it, otherwise it will be broke! :twisted:

---

