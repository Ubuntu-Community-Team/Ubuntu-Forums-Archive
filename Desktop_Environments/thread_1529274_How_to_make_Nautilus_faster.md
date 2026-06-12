---
title: "How to make Nautilus faster?"
date: 2010-07-12
forum: Desktop Environments
---

### Post by paulsp on 2010-07-12
One of the most common tasks I perform is browsing for files. I have always wanted my file manager to be lightning fast. That is, I open it  and it loads directories instantly. No waiting, just opening them right away. This remained always a wish, as in Windows and Ubuntu on a variety of machines I always see that it takes a little while for the program to load directories. I am not talking about folders with thousands of files or anything special. However, I have seen others who have Windows (XP in this case), and their Explorer opens right away. Browsing folders is very much instant.

Is there any way to achieve the same in Nautilus? The other computer is not very modern or super fast, at all. 

I have a laptop with SSD drive which I hoped would speed up this process, but this is not the case. On both my laptop and desktop I often see the 'loading' symbol, and files often appear after the folder view has opened (they just appear all of a sudden). This happens with folders I rarely visit but also with folders I often open.

How are others' experiences? Can Nautilus be instant? Is this a configuration tweak or hardware issue?

Thanks for any help.

---

### Post by mister_p_1998 on 2010-07-12
You could turn off preview in Nautilus...
edit, preferences, preview - show thumbnails - never


Steve

---

### Post by dzon65 on 2010-07-12
You can always replace it with thunar or pcmanfm.If you still want to speed up things,you could always use openbox (or others) as WM.

---

### Post by paulsp on 2010-07-12
Turning previews OFF makes it quite faster indeed. I tried it before but didn't see much difference. Now it seems quite fast indeed. Thanks for the tips!

Now, the situation of not seeing image previews is OK in MOST cases, but sometimes (meaning once a day) I'd need those previews. Is there some way to rapidly change this setting? I have seen this discussion:

[http://art.ubuntuforums.org/showthread.php?t=1436307](http://art.ubuntuforums.org/showthread.php?t=1436307)

And they want exactly what I'm looking for (a button to switch the view with one click), but I do not see this solution being found. Anybody any idea?

---

### Post by ellaivarios on 2011-06-21
> **paulsp said:**
> Turning previews OFF makes it quite faster indeed. I tried it before but didn't see much difference. Now it seems quite fast indeed. Thanks for the tips!

Now, the situation of not seeing image previews is OK in MOST cases, but sometimes (meaning once a day) I'd need those previews. Is there some way to rapidly change this setting? I have seen this discussion:

[http://art.ubuntuforums.org/showthread.php?t=1436307](http://art.ubuntuforums.org/showthread.php?t=1436307)

And they want exactly what I'm looking for (a button to switch the view with one click), but I do not see this solution being found. Anybody any idea?


--------------

Yes, what you need to do is simply write a script for nautilus and put it in gnome2>nautilusscripts or something like that in your file system directories if it is going to be Nautilus integrated... but that's a lot of work. Instead, my suggestion would be that you just make a simple script (and save it anywhere in your computer) that acts as a "preferences" switch for nautilus, and then go to system,preferences,keyboard shortcuts and assign a keyboard combination pointing to run that (.sh) script (i.e <CTRL>+T) "T" for Thumbnails so you can remember it, LOL), I'm a shortcut maniac myself. You might have to press F5 to refresh after each time, but that should be all. (Make sure you go into the script preferences and make it executable.)

If you don't know how, send me a message and maybe I'll do something for you, but I make no promises -- I am no GURU.

---

