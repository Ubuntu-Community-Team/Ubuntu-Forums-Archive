---
title: "[SOLVED] some fonts really small when using my TV as monitor"
date: 2008-10-20
forum: Desktop Environments
---

### Post by davidmaxwaterman on 2008-10-20
Hi,

The subject says it all really.

I'm using Ubuntu 8.04.1, but I'm fairly sure it doesn't make much difference.

When I use my 1920x1200 HP flat panel, everything looks fine, but when I use my 1360x768 LG TV, some fonts are rendered really small.

The font in this text area, for example, is just fine. The menu font on Firefox's menu bar, bookmarks bar, text in the tabs, the 'Prefix' drop-down menus and 'Title' and 'Check if Already Posted' text input areas are really small (various other items are small too).

Most notably, when I type my username to log in, it is echoed in the really small font.

It seems like the 'really small' font is always the same one.

How can I fix this?

Max.

---

### Post by Pauligrinder on 2008-10-20
I'm kind of having the same problem on my secondary computer, which is running Xubuntu 8.0.4.1. On my main screen though, on which my primary computer renders it all properly. I suspect this has to do with Nvidia drivers, because before I installed the latest "new-legacy"-driver for their site, it was fine (except I couldn't get my resolution above 640x480 on my monitor, on which I usually have 1400x1050).
- I have a Geforce 7600gt on my primary comp, has worked perfectly all the way, and Geforce 2 MX400 on the other one (I know, it's from the stoneage, as is the entire comp), with aforementioned problems. 
Now the resolution's fine, but some fonts are simply too small to read. It seems like they're stuck on the same amount of pixels as they used in the smaller resolution, or something like that.
Hope someone can help with this.

---

### Post by davidmaxwaterman on 2008-10-25
I fixed this using clues from [here]("http://ubuntuforums.org/showthread.php?t=423438"). Specifically, I added these options to the "Screen" section of my xorg.conf

```
    Option         "UseEDIDDpi" "False"
    Option         "DPI" "90x88"
```

HTH,

Max.

---

