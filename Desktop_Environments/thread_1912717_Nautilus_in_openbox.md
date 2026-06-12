---
title: "Nautilus in openbox"
date: 2012-01-21
forum: Desktop Environments
---

### Post by stevepoppers on 2012-01-21
Hi, I'm using openbox on Ubuntu 11.04. I'd like to continue using nautilus, but of course it takes over the desktop and covers up my feh wallpaper. I found this thread on the crunchbang forums ([http://crunchbanglinux.org/forums/topic/84/using-nautilus-under-openbox/](http://crunchbanglinux.org/forums/topic/84/using-nautilus-under-openbox/)) and implemented these commands.

# Disable Nautilus desktop.
gconftool-2 -s -t bool /apps/nautilus/preferences/show_desktop false &
# Do not let Nautilus set the background image.
gconftool-2 -s -t bool /desktop/gnome/background/draw_background false &

But for some reason, nautilus still blacks out the wallpaper when run and when I log in. I asked on that thread and grabbed a bit of newer crunchbang code to make it work, but it's basically the same thing with the same result. This is *really* confusing because I'm looking in gconf-editor, and nautilus is definitely set to *not* set or draw the background.

What's causing this and how do I stop it?

---

### Post by mcduck on 2012-01-21
Simple fix, edit your menu and change the command to launch Nautilus to "nautilus --no-desktop".

---

### Post by Sector11 on 2012-01-21
Install Crunchbang!  :lolflag:

---

### Post by okt on 2012-01-21
Do as mcduck has described,

or you can change the default functionality:

Launch 'gconf-editor'

/ > apps > nautilus > preferences

toggle 'show_desktop'

/ > desktop > gnome > background 

toggle 'draw_background'

Are both of those toggled to false?

---

### Post by malspa on 2012-01-21
> **okt said:**
> Do as mcduck has described,

or you can change the default functionality:

Launch 'gconf-editor'

/ > apps > nautilus > preferences

toggle 'show_desktop'

/ > desktop > gnome > background 

toggle 'draw_background'

Are both of those toggled to false?

Yeah, seems that those steps should do the same thing as the commands stevepoppers found in the Crunchbang forum thread:

> # Disable Nautilus desktop.
gconftool-2 -s -t bool /apps/nautilus/preferences/show_desktop false &
# Do not let Nautilus set the background image.
gconftool-2 -s -t bool /desktop/gnome/background/draw_background false &

I'd take a look in gconf-editor and make sure those two keys are toggled to off.

---

### Post by malspa on 2012-01-21
> **stevepoppers said:**
> But for some reason, nautilus still blacks out the wallpaper when run and when I log in.

For running Nautilus, **nautilus --no-desktop** works for me here in 10.04 (Openbox, with feh). This even though in gconf-editor I have a check mark next to apps>nautilus>preferences>show_desktop, and a check mark next to desktop>gnome>background>draw_background.

I have those turned on because I also use GNOME in 10.04, not just Openbox.

But, regarding when you log into Openbox: This may be a stupid question, but do you have a command to start feh in your ~/.config/openbox/autostart.sh? If not, maybe that's the problem for when you log in.

I'm using xfce4-panel and also feh in Openbox in 10.04. When I first log into an Openbox session, I get a black screen. Then xfce4-panel appears, and then my wallpaper. So I suppose GNOME takes over the desktop, but then feh takes over (???). Which is okay if that's what's happening.

At the end of my ~/.config/openbox/autostart.sh, I have:

```
(sleep 2 && xfce4-panel) &

#My wallpaper (random wallpaper script - calls wallpaper.sh)
(sleep 3 && /home/steve/wallpaper-loop.sh) &
```

My wallpaper-loop.sh calls wallpaper.sh, which starts feh. So if you already have a command to start feh in your autostart.sh script, maybe using a **sleep** command would be helpful.

---

