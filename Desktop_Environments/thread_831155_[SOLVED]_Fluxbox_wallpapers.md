---
title: "[SOLVED] Fluxbox wallpapers"
date: 2008-06-16
forum: Desktop Environments
---

### Post by Inxsible on 2008-06-16
I have a Debian core + Fluxbox install. I can set the wallpapers using feh.

But when I restart fluxbox, or reboot or even restart X, I get this message ```
fbsetting: No previous wallpaper recorded for display 0:0
```How would I make sure that my wallpaper stays even after reboot?

---

### Post by snowpine on 2008-06-16
Hi Inxsible,

Easy. Whatever code you used to set the wallpaper, simply add it to the ~/.fluxbox/startup file (but not the very end of the file, read the comment lines and it will be obvious) with a space and an ampersand at the end.

For example:

```
fbsetbg -f ~/pictures/wallpaper.jpg &
```

I think that will do the trick, but I'm on Windows at work at the moment. :(

---

### Post by Inxsible on 2008-06-16
> **snowpine said:**
> Hi Inxsible,

Easy. Whatever code you used to set the wallpaper, simply add it to the ~/.fluxbox/startup file (but not the very end of the file, read the comment lines and it will be obvious) with a space and an ampersand at the end.

For example:

```
fbsetbg -f ~/pictures/wallpaper.jpg &
```I think that will do the trick,.... Does that mean that I will have to do this every time I change the wallpaper?

> **snowpine said:**
> ......but I'm on Windows at work at the moment. :(Me too. So I can only try out your suggestion after I get back home:)

---

### Post by snowpine on 2008-06-16
> **Inxsible said:**
> Does that mean that I will have to do this every time I change the wallpaper?

If you use my method, my method is how you will change the wallpaper every time! :)

I really am not familiar with feh, sorry. I have a hunch that maybe you could add feh to .fluxbox/startup (instead of the code I listed above) and then it would load every time you boot and set the background?

This would be similar how the background is set on my Fluxbuntu system. I have a program called rox-filer that automatically starts up and sets the wallpaper (among other things). Same idea.

---

### Post by jjgomera on 2008-06-16
Snowpine is fine:

[http://ubuntuforums.org/showthread.php?t=116759](http://ubuntuforums.org/showthread.php?t=116759)

Section **Customization Tips and Tricks**

---

### Post by snowpine on 2008-06-16
> **jjgomera said:**
> Snowpine is fine:

[http://ubuntuforums.org/showthread.php?t=116759](http://ubuntuforums.org/showthread.php?t=116759)

Section **Customization Tips and Tricks**

Thanks JJGomera, great thread!

---

