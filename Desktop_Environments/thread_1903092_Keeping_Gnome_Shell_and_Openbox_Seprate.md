---
title: "Keeping Gnome Shell and Openbox Seprate"
date: 2012-01-01
forum: Desktop Environments
---

### Post by brndn on 2012-01-01
Hi everyone! (first post :D )

I've been playing around with Linux, especially Ubuntu, for quite a while now, and I just got a new laptop.  I installed Ubuntu 11.10, and installed Gnome shell. I like it. Sometimes, however, I prefer to work in more of a minimalist "mode." For this, I like Openbox. (I know they're pretty much on opposite ends of the spectrum :P ) I installed Openbox such that at the login menu, I choose between Gnome and Openbox sessions. 

My question is, how do I keep software and settings distinct? For example, I like Nautilus as my default file manager on Gnome (use it for the wallpaper and desktop, too) but in Ob, I'd rather use PCManFM, and nitrogen to manage the wallpapers. Is it even possible to not load any Gnome dependencies while in the Openbox session?

---

### Post by Buntero on 2012-01-04
Hi

I don't know how the default openbox session works, but you can create your own session if you want more control.

Create following file in /usr/share/xsessions:

[Desktop Entry]
Name=somename
Type=XSession
Exec=openbox

You can then choose somename as your session.

To run more apps at startup use  ~/.config/openbox/autostart.sh. I would recommend you use nm-applet to magically connect to the internet (you need a notification area for it to work properly, so run a panel or a standalone systray (such as stalonetray)).

Have fun!

---

### Post by mcduck on 2012-01-04
> **brndn said:**
> Hi everyone! (first post :D )

I've been playing around with Linux, especially Ubuntu, for quite a while now, and I just got a new laptop.  I installed Ubuntu 11.10, and installed Gnome shell. I like it. Sometimes, however, I prefer to work in more of a minimalist "mode." For this, I like Openbox. (I know they're pretty much on opposite ends of the spectrum :P ) I installed Openbox such that at the login menu, I choose between Gnome and Openbox sessions. 

My question is, how do I keep software and settings distinct? For example, I like Nautilus as my default file manager on Gnome (use it for the wallpaper and desktop, too) but in Ob, I'd rather use PCManFM, and nitrogen to manage the wallpapers. Is it even possible to not load any Gnome dependencies while in the Openbox session?

Openbox shouldn't load any Gnome dependencies at all unless you configure it to do so.

What does your autostart.sh for Openbox look like?

And if you don't want to use Nautilus in Openbox, just don't use it. :) It shouldn't load unless you start it yourself (and even then you can just start it with "nautilus --no-desktop" to prevent it from taking over the desktop when started).

---

### Post by brndn on 2012-01-05
My autostart.sh is clean of anything Gnome - I was wondering if, for example, my default file manager could be separate for different sessions. However, I'm starting to use Openbox less and less and tweak my Gnome session so it isn't so 'heavy,' for lack of a better word. Thanks!

---

### Post by mcduck on 2012-01-06
Sure, the file manager should work completely separate from what's used on Gnome. And you shouldn't need to do anything to make that happen. Just make sure the file manager you have added to the Openbox menu is the one you want to use.

---

