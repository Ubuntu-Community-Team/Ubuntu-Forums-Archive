---
title: "Default background flashes after login"
date: 2008-03-16
forum: Desktop Effects &amp; Customization
---

### Post by stealth86 on 2008-03-16
OS: Kubuntu 7.10 w/ KDE 3.5

I've installed a new KDM theme and a new splash screen. Both work great, but after I login but before the KDE splash screen starts up, the default kubuntu background comes up for a few seconds.

It looks really ugly, and I'm wondering how I would change this? I've seen some posts about a similar issue with GDM, but I've yet to find anything regarding KDM.

Thanks!

---

### Post by stealth86 on 2008-03-16
So I solved my own problem. Not sure if it's the best solution but here it is if someone else is interested.

I moved the background image I wanted to see to /usr/share/wallpapers.

Then I edited /etc/kde3/kdm/backgroundrc. I changed the Wallpaper line to be the name of the image I had just moved to /usr/share/wallpapers above.

Hopefully that saves someone else a few minutes of their time.

---

