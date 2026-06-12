---
title: "dual screens enlightenment E17"
date: 2009-05-07
forum: Desktop Environments
---

### Post by zigga15 on 2009-05-07
Hey all,

I have recently put E17 on my ubuntu 9.4 - it is great and love it however I am having some problems with my dual monitors.

I am using a nvidia 8800gts with the "twinview" option.

The problem is that I cannot get the secondary screen to switch virtual desktops, and when I try to do it through the menus in enlightenment it can't seem to find the resolutions (maybe because of my xorg.conf.

Can anyone please help? :)

```
$ xrandr

Screen 0: minimum 3360 x 1050, current 3360 x 1050, maximum 3360 x 1050
default connected 3360x1050+0+0 0mm x 0mm
   3360x1050      50.0* 
```

Cheers

Dan

---

### Post by zigga15 on 2009-05-07
bumpity bump

---

### Post by zigga15 on 2009-05-07
Anyone??? can someone point me in the direction of the correct forum or something?

---

### Post by mu22le on 2009-05-08
What repository are you using? Or did you compile from source? (if so, when?)

---

### Post by zigga15 on 2009-05-09
I followed this guide: [http://ubuntuforums.org/showthread.php?t=546746](http://ubuntuforums.org/showthread.php?t=546746)

basically i used the cvs repo and built it with the easy_e17 shell script.

Thanks for your help.

~ Dan

---

### Post by zigga15 on 2009-06-11
a big huge late reply (Sorry been busy with university stuff).

When I change the key binding to flip both screens on both monitors, they both flip.

So I am guessing that everything is working, its just the settings however I can't for the life of me work out how to have a pager on both my monitors which flips each screen independently.

Any help would be great -- not sure how many people have E17, or dual monitors but hopefully there is a few people out there who can help :)

~ Dan

---

### Post by peepingtom on 2009-06-11
> **zigga15 said:**
> When I change the key binding to flip both screens on both monitors, they both flip.

I think they both flip because you're using twinview, people freak out when their compiz cube spans 2 monitors so you might want to search for their solutions. You can definitely use separate X screens to work around this. 
[https://help.ubuntu.com/community/NvidiaMultiMonitors](https://help.ubuntu.com/community/NvidiaMultiMonitors)
It is not an ideal situation, you have to tweak it. You can't drag windows between monitors this way. Maybe xinerama is the best of both worlds but I doubt it.
Sorry, i'm not an Enlightenment user. OpenBox Rules!!! :p

---

### Post by zigga15 on 2009-06-12
yea openbox is the next thing to try when I get some spare time :) -- thanks for your help!

~ Dan

---

