---
title: "Different background images for different desktops?"
date: 2012-10-29
forum: Desktop Environments
---

### Post by yavamoni on 2012-10-29
Is it possible to set different background images in the different desktops?

I am using Ubuntu 12.04, and I can't seem to find if this is possible or not. 

Thanks a bunch for reading/replying!

---

### Post by flint5 on 2012-10-30
Yes it is possible.
There is a link, how to make that:
[http://askubuntu.com/questions/75998/is-it-possible-to-have-a-different-background-for-each-workspace](http://askubuntu.com/questions/75998/is-it-possible-to-have-a-different-background-for-each-workspace)

---

### Post by yavamoni on 2012-10-30
Thanks a bunch! I am offf to try :-)

---

### Post by yavamoni on 2012-10-30
Thank you for your help. When I tried it I got the different backgrounds, but the pointer was not working inside any windows, so I reverted back to normal. I suppose I should do some extra reading on compiz to understand the problem and solve it.

---

### Post by flint5 on 2012-10-31
You don't need to make some extra readings, it's normal that pointer don't work inside any windows, because you turned off desktop icons, and that makes the desktop unclickable, except unity launcher and panel who continue to operate normally.
If you turn on desktop icon, the wallpaper option in compiz  will turn off.

---

### Post by yavamoni on 2012-10-31
First of all, thank you for your help.

There is something I don't understand in your message, so please bear with me. It may be that you are not understanding me, so I'll try to explain.
> **flint5 said:**
> You don't need to make some extra readings, it's normal that pointer don't work inside any windows, because you turned off desktop icons, and that makes the desktop unclickable, except unity launcher and panel who continue to operate normally.
If this is "normal", how am I supposed to work with the computer? 
It is not that the pointer doesn't work **outside** the widnows, but **inside** them. It is a big pain in the rear to work in almost any program with no mouse control (tab did let me turn the compiz off, for instance) - to almost impossible in graphics programs!

> **flint5 said:**
> 
If you turn on desktop icon, the wallpaper option in compiz  will turn off.
If what you say is that I won't be able to correct this, this is too high a price to pay for aesthetical pleasure of having different backgrounds...

---

### Post by flint5 on 2012-10-31
Sorry for the misunderstanding, when you wroth that you pointer was not working inside any windows, i meant that the pointer was not working under desktop workspaces.

When you disable the show_desktop_icon in dconf or in Ubuntu Tweak, you can't put icons on the desktop workspace, and the desktop is unclickable, but any others like unity launchpad and panel, windows and applications works normally (try it with Ubuntu Tweak, and you will see what i mean).

With the 'second Quote' i meant when you turn on the show_desktop_icon in dconf or Ubuntu Tweak, it disables the wallpapers option in compiz.

I tested this different background twice, and i had no issues with my pointer in any windows, everything has worked properly.

---

