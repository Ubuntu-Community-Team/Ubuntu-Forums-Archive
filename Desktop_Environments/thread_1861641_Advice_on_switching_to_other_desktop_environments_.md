---
title: "Advice on switching to other desktop environments? [especially from Gnome to Xfce]"
date: 2011-10-15
forum: Desktop Environments
---

### Post by MarjaE on 2011-10-15
So far I've been using Gnome 2/Classic. I am considering switching to Xfce, either with Ubuntu or with another distribution. I often need to switch between two windows to compare two documents. Xfce seems to enable this as easily as Gnome 2/Classic and more easily than Unity. I didn't have much trouble disabling the visible-on-mouseover features either.

Still, I'm open to trying other desktop environments before settling on just one.

So I am also trying to decide whether to use a fresh install of Xubuntu, a fresh install of another distro - one of my friends recommended Debian - or maybe a fresh install of some hybrid Ubuntu. I mean, I like Xfce so far, but I'd rather keep my options open.

Another issue is how to back up settings, such as internet settings, so it's easier to get things working again after the reinstall.

---

### Post by gsmanners on 2011-10-15
I would for sure keep a backup of your /home folder somewhere handy if you have the space for it (external TB drive works great for this).

There's not a whole lot of difference between Xfce and old Gnome, aside from a few esoteric features that Xfce tends to be a bit behind the curve on implementing. The biggest change in Xfce lately is definitely the gtk3 stuff (Gnome games, Calculator, File Roller and a number of other Gnome apps have switched to gtk3). The good news is that there is a theme that implemented both gtk2 and gtk3 (called "greybird" which is the default for Xubuntu). The bad news is if you ever want to use something other than greybird, you might want to keep gtk3 in mind.

I recently did something like this:

```
cp -r /usr/share/themes/greybird/gtk-3.0 ~/.config
```

That'll prevent you from falling back into the ugly default gtk3 theme (Raleigh or something like that).

The menu in Xfce is back to being a pain to edit, but it's no big deal if all you want to do is hide a few entries.

The Places plugin is working again, and you can drag and drop your "window buttons" (task list). :D

Leafpad is the new default (which I like better than Mousepad since I never used the recent documents menu anyway).

The pic viewer is gthumb by default. I would avoid using ristretto (as that sucker has been hanging on me, but I think I prefer gthumb anyway).

I always install audacious and remove gmusicbrowser, but that's just me maybe.

I also removed indicator-messages-gtk2 because I never use that IM stuff anyway. I like just having the sound and networking in the appindicators.

I also use htop rather than the standard "task manager".

Well, this is how I like things, anyway. YMMV

---

