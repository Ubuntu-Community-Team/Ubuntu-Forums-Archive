---
title: "Desktop Picture?"
date: 2011-05-09
forum: Desktop Environments
---

### Post by Esteem on 2011-05-09
Is it possible to change desktop picture on every desktop I have? ^_^
With regards, David

---

### Post by Copper Bezel on 2011-05-09
There's a Compiz plugin for this, but it's a bit buggy, at least in 10.10; I haven't upgraded, but under a normal Gnome session, I have to switch to a VT and back to get the wallpaper to initialize properly.

It also requires turning off the Nautilus desktop through gconf-editor, which means that you won't have desktop icons, although you can get the folderview screenlet or something like it to get back *some* of this functionality.

If you still want to try it: In CompizConfig Settings Manager, activate and configure the Wallpaper plugin. In gconf-editor, navigate to apps > nautilus > preferences and untick the key "show_desktop". You might also need to untick all of the items under nautilus > desktop.

I use it, and I find it helpful for keeping my tasks organized and feeling a little less confined in some sense, but I also don't use an ordinary Gnome session (making it possible to fix the wallpaper initializing bug) and haven't used desktop icons for some time (preferring just to keep a Thunar window up for whatever I'm working with.)

---

### Post by Esteem on 2011-05-09
Thanks for your help, it's useful, but I am a newb on ubuntu :) I'll try it someday, when I get used to new OS :)) 
(Now I just though there's some kinky program that will do it for me :))

---

### Post by Copper Bezel on 2011-05-09
That's fair. = ) Yeah, KDE does this as a built-in feature, but Gnome makes you work for it a little, which is unfortunate.

---

