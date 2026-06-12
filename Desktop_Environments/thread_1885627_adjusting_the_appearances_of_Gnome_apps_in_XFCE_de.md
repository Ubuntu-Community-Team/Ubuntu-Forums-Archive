---
title: "adjusting the appearances of Gnome apps in XFCE desktop"
date: 2011-11-23
forum: Desktop Environments
---

### Post by sidewalkcynic on 2011-11-23
I found XUbuntu to be relatively more tolerable than the new Gnome Shell, but I need my Gnome apps like Nautilus, Gedit, and Synaptic, to keep me happy. Somehow in the mix of learning how to adjust the appearances the XUbuntu way I toggled something that prevents the themes in those Gnome apps.

I have learned how to edit the gtkrc files in the .themes directory to adjust the themes, but some where before that I toggled something in one of the settings editors, or something that I cannot remember.

---

### Post by Toz on 2011-11-23
Have a look at [http://ubuntuforums.org/showthread.php?p=11452395]("http://ubuntuforums.org/showthread.php?p=11452395"). You need to use an xfce gtk3 theme (like greybird) or make manual configuration changes to ~/.config/gtk-3.0/*

---

### Post by cmcanulty on 2011-11-23
I have been working a lot on getting xfce4 like gnome 2. It seems a bit harder to configfure and somewhat buggy ex no matter what I set font and cursor to they stay tiny. But here is a link to some screenshots of my work fso far and a list of my installed pkgs there now is a package to gnomeify the xfce panel icons. Check out post #34 on this thread and let me know what you think and any hints or ideas to improve.I just posted a new reply with the results of my many attempts to get a gnome classic desktop and I think I am now very close. Please look at my screenshots and tell me what you think. I still have had no luck getting a large black cursor like I had. The option is listed but doesn't work in unity or xfce4. Here is a link to the thread it is post #34
[http://ubuntuforums.org/showthread.p...5#post11483985](http://ubuntuforums.org/showthread.p...5#post11483985)
I think it looks pretty good btu a whole new bunch to learn,

---

### Post by sidewalkcynic on 2011-11-24
That link doesn't seem to work - it sends me to the forum's front page.


> **Toz said:**
> Have a look at [http://ubuntuforums.org/showthread.php?p=11452395]("http://ubuntuforums.org/showthread.php?p=11452395"). You need to use an xfce gtk3 theme (like greybird) or make manual configuration changes to ~/.config/gtk-3.0/*

I am using Clearlooks as my themes base, and I went and made eight color schemes to it already ! ! ! !

Okay, I'll search for gtk3 theme, and redo my eight color themes - thanks.

greybird is the only gtk3 theme on the list - what a pain - I'll work with it, because i am not going through all that crap of going through the theme website. It looks like greybird is set up to be the learning environment I need - thanks again.

---

### Post by neu5eeCh on 2011-11-24
I'm not sure, but Shiki might be gtk-3.0. You can find shiki via Synaptec.

---

### Post by sidewalkcynic on 2011-11-24
I'm having trouble finding the adjustment scripts, because there are several options and the obvious is not doing it.

I noticed that when I change the name of the "greybird" folder that I copied into my .themes folder I have the same problem as before - the gnome apps; Nautilus, gedit, and Synaptic, don't read it, or whatever, and go to the default Redman theme.

---

