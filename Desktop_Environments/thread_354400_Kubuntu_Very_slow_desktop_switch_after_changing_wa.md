---
title: "Kubuntu: Very slow desktop switch after changing wallpaper"
date: 2007-02-05
forum: Desktop Environments
---

### Post by diamond on 2007-02-05
This may just be one of those things that I can't do anything about, but I'm curious if anyone else has noticed similar issues.

I'm running Kubuntu Edgy (actually, I installed it as Ubuntu and recently switched by installing the kubuntu-desktop package) on a Dell Inspiron 600m. I'm running at 1400x1050 resolution, I have 9 virtual desktops, and desktops 7, 8 and 9 are set to "slideshow" mode, all drawing from the same pool of wallpapers. It's a rather large list (almost 2000 files), and each one is set to change every 30 minutes.

I've noticed that, after one of the wallpapers changes, the first switch to and away from that desktop is *very* slow; the machine essentially locks up for about 5-10 seconds. Any subsequent changes are instantaneous, until the wallpaper changes again.

At first I thought the problem was due to the large number of files I have in each desktop's slideshow list. So I tried switching one desktop manually to a single wallpaper. But the same thing happened. I even tried choosing a picture from a directory with very few other pictures -- thinking that, for some unimaginable reason, the large size of the picture's home directory might be slowing things down. No luck.

So I'm stumped. It seems that, no matter what I do, whenever I change the wallpaper on a given desktop, the first time I switch to that desktop, I'll have to endure a complete machine lockup for about 5 or 10 seconds, and once more when I switch away from it. Does anyone have any ideas what might be going on? Has anyone else encountered this problem?

---

### Post by shareMenaPeace on 2007-02-05
Can you somehow run the slideshow application from terminal to find an error message or info?

---

### Post by diamond on 2007-02-06
> **shareMenaPeace said:**
> Can you somehow run the slideshow application from terminal to find an error message or info?

I'm not sure how to do that. I don't think it's a separate application; I believe it's built into kdesktop.

Anyway, as I said, the problem still happens when I switch the desktop manually. So I don't think that's the problem.

It's probably just a performance limitation I'll have to live with. Oh well.

---

