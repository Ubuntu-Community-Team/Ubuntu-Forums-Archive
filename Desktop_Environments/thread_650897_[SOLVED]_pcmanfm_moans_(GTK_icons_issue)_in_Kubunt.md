---
title: "[SOLVED] pcmanfm moans (GTK icons issue?) in Kubuntu Gutsy"
date: 2007-12-26
forum: Desktop Environments
---

### Post by TeaSwigger on 2007-12-26
Well with the dust well settled I've finished a fresh install of Kubuntu Gutsy. I've also installed Fluxbox to use as my regular wm. Keeping things light-ish, I've installed pcmanfm from the repos to use as fm with Fluxbox. Ah but upon firing up pcmanfm, it invariably throws up a warning dialog first. Here it is:

> GTK+ icon theme is not properly set

This usually means you don't have an XSETTINGS manager running.  Desktop environment like GNOME or XFCE automatically execute their XSETTING managers like gnome-settings-daemon or xfce-mcs-manager.

If you don't use these desktop environments, you have two choices:
1. run an XSETTINGS manager, or
2. simply specify an icon theme in ~/.gtkrc-2.0.
For example to use the Tango icon theme add a line:
gtk-icon-theme-name="Tango" in your ~/.gtkrc-2.0. (create it if no such file)

NOTICE: The icon theme you choose should be compatible with GNOME, or the file icons cannot be displayed correctly.  Due to the differences in icon naming of GNOME and KDE, KDE themes cannot be used.  Currently there is no standard for this, but it will be solved by freedesktop.org in the future.

So I tried emelfm2, and guess what, no icons. No other GTK apps are having any issues. Gnome icons are installed. Of course I don't want to install and run needless stuff like gnome-settings-daemon. Not that I know how. I tried installing Tango icons - there may be more icons on this PC than you'll find at an Ancient Greek museum - and putting gtk-icon-theme-name="Tango" in a ~/.gtkrc-2.0 file. Doesn't work!

Anyone know how to fix this? Ideas?

---

### Post by TeaSwigger on 2007-12-28
*checks pcmanfm, it's still crabbing about it every time I open it.

*comes in to dust.

---

### Post by TeaSwigger on 2007-12-31
After a lot of wasted time researching stuff about icons and paths, it turns out the solution was rather simple. In the hopes of saving somebody else a lot of time, I'll post it. What an idea...

If using Kubuntu:

What does not work is to add the line to ~/.gtkrc-2.0 as the dialog advised. Nor adding it to a ~/.gtkrc.

What does work is to add the line gtk-icon-theme-name="Tango", or in my case:

```
gtk-icon-theme-name="GNOME"
```

to the file ~/.gtkrc-2.0-kde. 

If using another window manager on Kubuntu, like Fluxbox:

Follow the advice to add 

```
gtk-icon-theme-name="GNOME"
```

to ~/.gtkrc-2.0, and also add it to ~/.gtkrc-2.0-kde.

That's how to get pcmanfm from the repos to work without moaning, and how to get icons to show up in emelfm2, and possibly other icon-deprived gnome/GTK apps to work right in KDE/Kubuntu.

The little down side is that you'll probably have to do it over and over every time you change the theme in the control center as it probably over-writes the ~/.gtkrc-2.0-kde file, and if you use theme switchers in another window manager, they probably overwrite the ~/.gtkrc-2.0 file too. If this is so, I don't know how to make it permanent, because using a ~/.gtkrc.mine file doesn't work. At any rate as it could be a factor using a number of apps in the ubuntu repos with Kubuntu, it's possibly a compatibility thing the Kubuntu devs should have made provision for. I know, send a bug... all these folks sending bugs about, creeps me out tho' :p

---

### Post by urukrama on 2007-12-31
Sorry that I'm a bit late with this, TeaSwigger, but I saw [this]("http://suseforums.net/index.php?showtopic=18336") a while ago. Is this related, and could this also work?

---

### Post by TeaSwigger on 2008-01-11
Thank you urukrama for the kind reply.

---

