---
title: "Some WMII Questions"
date: 2008-07-22
forum: Desktop Environments
---

### Post by Forlornity on 2008-07-22
Well, seeing as all resources on WMII's website appear to be 404ing at the moment, I need somewhere to ask my noob questions.
First, lemme get this out of the way: WMII is awesome (well, it isn't... but that's a whole different window manager), and I'm really enjoying using it, very efficient and nice looking for those minimalists in our midst.

My first question: Is it possible to have a persistent window appear across all tabs in WMII, so I could, say, have a small conky bar appearing at the bottom of my screen at all times.

Next: Although I'm sure I could figure it with a man page and/or some googling, how does one give tabs on WMII friendly names?

Third: Is it possible to assign arbitrary keys for extra tabs?
In that I mean still using the same modifier key, but with other keys opening other tabs (such as Alt+` opening a '`' tab possibly, for instance)

Much as I'm sure I'll have more questions soon enough, that'll have to do for now.

Thanks, Forlornity

---

### Post by Forlornity on 2008-07-23
Really sorry about the double post,
The really important one to me is the first question, could someone even inform me as to whether this is possible in the repos' build of WMII or not?

Thanks, Forlornity

---

### Post by DeathOnJuice on 2008-07-24
Believe me, I have questions as well, having switched yesterday. I can help with two of your questions, though, and I have a vague idea about 1.

2. To give windows "friendly" tags, press Mod(Alt)-Shift-t, then type the tags you wish to give it, separating different tags with +s. You'll probably only need one tag, though. To go to that tag, press Mod-t, then type it in.

3. Really, it would be easy enough to do what you said by pressing Alt-t, `, then enter. However, to set more hotkeys, copy your /etc/wmii-3.5/wmiirc to /home/yourusernamehere/.wmii-3.5/wmiirc. Look inside it and find the long section with entries in this format:

Key $MODKEY-Shift-$UP
    wmiir xwrite /tag/sel/ctl send sel up

Then add (this is an educated guess; I don't know whether the ` will work:
Key $MODKEY-`
    wmiir xwrite /ctl view "`"

Looking at the rest of this file should give you more information about Wmii. I haven't gone through most of it myself yet, though.

1. My vague idea for 1 - somehow fiddle with wmiirc so that any tags created will be assigned to the window you want to be persistent.

My question:

How do you assign default file handling programs? What file manager is usually used with wmii? I'm trying out vifm, but when I open any file, including images, pdfs, Windows .exes, etc, it opens them in Vim, which doesn't work so well. In GNOME, it knows to open images with the image viewer, .exes with Wine, and so on. Any idea how to set this up in wmii/vifm?

Good luck.

---

### Post by DeathOnJuice on 2008-07-24
Bump. Is there usually a good guide on the wmii page? As the original post says, most of the links on that site are down.

---

### Post by DeathOnJuice on 2008-07-24
Bump.

---

### Post by LaRoza on 2008-07-24
> **DeathOnJuice said:**
> Bump. Is there usually a good guide on the wmii page? As the original post says, most of the links on that site are down.

wmii changed their site, and the new one isn't up fully yet.

For file manager, I use thunar and mc (mc is used in a terminal). Don't use nautilus.

> **Forlornity said:**
> 
My first question: Is it possible to have a persistent window appear across all tabs in WMII, so I could, say, have a small conky bar appearing at the bottom of my screen at all times.
You can give it multiple tags: [http://www.minixtips.com/2006/07/wmii-window-manager-for-minix-3.html](http://www.minixtips.com/2006/07/wmii-window-manager-for-minix-3.html)

(That article is for minix, but it works the same of course)

I haven't spent much time customizing wmii, so my skills are limited with it and I am using xmonad at the moment (which is very similiar to wmii)

---

### Post by DeathOnJuice on 2008-07-24
Thanks. I suppose I'll wait on the site for further tips and try out Thunar (mc, like vifm, couldn't handle anything but text files). I might also try ratpoison and xmonad, but I've heard that wmii is the best of all the tiling wms.

---

### Post by Forlornity on 2008-07-29
Thanks a lot LaRoza, that article really helped me get my wmiilegs, and thanks to you too DeathOnJuice, but /etc/wmii-3.5/wmiirc doesn't exist for me, where else might it reside do you think?

Thanks, Forlornity

---

### Post by mali2297 on 2008-07-29
> **Forlornity said:**
> ... but /etc/wmii-3.5/wmiirc doesn't exist for me, where else might it reside do you think?


In the terminal, type
```

locate wmiirc

```
and see what comes up.

---

### Post by Forlornity on 2008-08-18
Quick note, the guide at [http://code.suckless.org/contrib/guide/wmii-3/guide-en/guide_en/](http://code.suckless.org/contrib/guide/wmii-3/guide-en/guide_en/) is back up again.

Also, it seems a friend of mine happens to be among the regular contributors at suckless.org, although I suspect he's a dwm only guy :P
Still, small world huh?

- Forlornity

---

