---
title: "Openbox, SLiM, and feh"
date: 2011-01-25
forum: Desktop Environments
---

### Post by Lunarll on 2011-01-25
Hello, I've recently started trying to mess around with my Linux system and try to reduce bloat. To this end I installed Openbox, SLiM, and feh (to manage backgrounds).

My main issue at the moment is that *autostart.sh* doesn't seem to run itself whether it is in "*~/.config/openbox*" or "*/etc/xdg/openbox*." So far I've tried
```

eval 'cat ~/.fehbg'
feh --bg-center "~/Pictures/Wallpapers/ruins.jpg"

```
in *autostart.sh* to no avail. I think that this might be an issue with SLiM's default configuration but I can't gather anything from the documentation because apparently, Ubuntu doesn't use a "*~/.xinitrc*" file (all the documentation I've seen refers to *.xinitrc* and I don't know what file replaces it in Ubuntu). 

The strange thing is that I am running in Openbox just fine - just the autostart.sh doesn't run at start. I've heard that there's a difference between running "*openbox*" and "*openbox-session*" but again I don't know what file to edit.

Any help for a solution would be much appreciated. Thanks for your time. ^^;

---

### Post by hhh on 2011-01-25
It's been awhile since I ran a standalone Openbox session in Ubuntu, but I'm sure others who currently are will chime in, so I'll post. Here are 3 links that should give you most of what you need to know...
[https://help.ubuntu.com/community/Openbox](https://help.ubuntu.com/community/Openbox)
[http://urukrama.wordpress.com/openbox-guide/](http://urukrama.wordpress.com/openbox-guide/)
[https://wiki.archlinux.org/index.php/Openbox](https://wiki.archlinux.org/index.php/Openbox)

Your autostart file should go in ~/.config/openbox. You need to add an ampersand to any command in it...
[http://urukrama.wordpress.com/openbox-guide/#Autostart](http://urukrama.wordpress.com/openbox-guide/#Autostart)

I'm pretty sure you don't need an .xinitrc file as you will log in to a standalone Openbox session from the login manager, but you can just create an .xinitrc file if you need one.

-edit- Oh yeah, having Feh's background persist is as simple as adding this to your autostart file...```
sh ~/.fehbg &
```

---

### Post by Lunarll on 2011-01-25
> **hhh said:**
> It's been awhile since I ran a standalone Openbox session in Ubuntu, but I'm sure others who currently are will chime in, so I'll post. Here are 3 links that should give you most of what you need to know...
[https://help.ubuntu.com/community/Openbox](https://help.ubuntu.com/community/Openbox)
[http://urukrama.wordpress.com/openbox-guide/](http://urukrama.wordpress.com/openbox-guide/)
[https://wiki.archlinux.org/index.php/Openbox](https://wiki.archlinux.org/index.php/Openbox)

Your autostart file should go in ~/.config/openbox. You need to add an ampersand to any command in it...
[http://urukrama.wordpress.com/openbox-guide/#Autostart](http://urukrama.wordpress.com/openbox-guide/#Autostart)

I'm pretty sure you don't need an .xinitrc file as you will log in to a standalone Openbox session from the login manager, but you can just create an .xinitrc file if you need one.

-edit- Oh yeah, having Feh's background persist is as simple as adding this to your autostart file...```
sh ~/.fehbg &
```

The background doesn't seem to persist at all. x.x
Instead, the background from SLiM just stays the same. If I do "*./autostart.sh*" the background turns out fine but I'd like it automated.

---

### Post by hhh on 2011-01-25
Did you look through the links I gave you?

---

### Post by Lunarll on 2011-01-25
> **hhh said:**
> Did you look through the links I gave you?

I have, they don't seem to have anything that solves my issue.

---

### Post by urukrama on 2011-01-25
To change the session SLIM starts, you need to edit your .xinitrc file and make sure it loads openbox-session. Have a look at the Arch Wiki page on SLIM for more info: [https://wiki.archlinux.org/index.php/SLIM](https://wiki.archlinux.org/index.php/SLIM)

---

