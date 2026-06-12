---
title: "kde and gnome warning, is this true?"
date: 2007-12-22
forum: Desktop Environments
---

### Post by faraz_k86 on 2007-12-22
ok i read this [here]("http://www.psychocats.net/ubuntu/kde")



Warning: having KDE and Gnome together means you'll have cluttered application menus full of KDE applications and Gnome applications. You may also run into some other cosmetic problems (the KDE QT look taking over some of your Gnome themes, a hidden file on your desktop that keeps appearing in Gnome after you've just logged out of KDE). One of the most common problems is the new desktop environment "taking over" the boot splash screen.


i think this was written for ubuntu edgy, is this still a common problem????


also ive heard people having 12 desktop enviornments, then they must really be cluttered up eh?

---

### Post by atomkarinca on 2007-12-22
I've had Gnome, KDE and E17 on Gutsy together and the only thing I can agree is that KDE applications do take up most of the applications menu. Other than that it was smooth.

---

### Post by faraz_k86 on 2007-12-23
so even if i am running gnome ecen then the kde applications will show up in the menu??

why is that, so can i open the kde aps in the gnome session.

and how much is the kde installation? like how many MB?

---

### Post by LaRoza on 2007-12-23
> **faraz_k86 said:**
> so even if i am running gnome ecen then the kde applications will show up in the menu??

why is that, so can i open the kde aps in the gnome session.

and how much is the kde installation? like how many MB?

```

sudo aptitude install kde-core

```

Is pretty light, and will not clutter your menus. You can always remove programs you don't want.

KDE apps do tend to stand out in menu's.

You can use KDE apps fine in GNOME, and vice versa.

-EDIT Size is 18 MB which is unpacked to 47.6.

(Nice avatar, I just bought the shirt for my brother's birthday next month)

---

### Post by faraz_k86 on 2007-12-23
is 18mb the size of kde-core or of kde-desktop?


lol, thx about my avatar. I am a huge fan of The Punisher.


lucky guy your brother is :)

---

### Post by LaRoza on 2007-12-23
> **faraz_k86 said:**
> is 18mb the size of kde-core or of kde-desktop?


lol, thx about my avatar. I am a huge fan of The Punisher.


lucky guy your brother is :)

kde-core, that is all you need.

---

### Post by thor228 on 2008-04-19
i have just tried installing kde and xfce on ubuntu and all seemed to be perfect until i turned the computer off and back on again and the boot splash screen had been taken over by first kubuntu then it said xubuntu before finally ending on the xubuntu style login screen despite the fact that i have set gnome as default.
i am running ubuntu 7.10.
if you go to the spychocats website and go on the tutorial to install kde it says about this problem and how to fix it except that the link to fix it is broken.
it would be useful to be able to fix this minor problem
[http://www.psychocats.net/ubuntu/kde]("http://www.psychocats.net/ubuntu/kde")

---

### Post by T-Virus on 2008-04-19
I just remember having both KDE and Gnome like few years ago and Gnome config files kept appearing on my KDE desktop which kind of didn't looked good. It worked no problem, just minor cosmetic issues.

I'm not sure but this might changed.

---

### Post by maxfisher05 on 2008-05-27
to change splash screens when you have multiple versions installed (kubuntu, xubuntu, etc.) use

$sudo update-alternatives --config usplash-artwork.so

and select the screen you want

---

