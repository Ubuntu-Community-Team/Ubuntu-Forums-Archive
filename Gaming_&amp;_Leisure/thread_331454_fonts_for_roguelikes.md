---
title: "fonts for roguelikes"
date: 2007-01-04
forum: Gaming &amp; Leisure
---

### Post by j19sch on 2007-01-04
Hi everyone,

I like playing roguelikes (crawl and adom), but I don't like the font the terminal runs in at the moment. I know how to change it, but I was wondering in what font other people are playing, so that I might try those out.
And related to this: how can I change the font of the terminal I get when I press CTRL+ALT+F1? (Don't know what's it called; I know it's a non X-windows terminal.) It's a nice way to play full screen. :D 

Thanks,
Joep

---

### Post by dolny on 2007-01-05
I'm just using monospace (size 8) and an xfce4-terminal (although I'm using KDE again) for my ADOM baby ;) and also for [http://www.accursed-lands.com](http://www.accursed-lands.com) - ahhh.

---

### Post by j19sch on 2007-01-05
I guess I'll checking out Accursed Lands later this weekend.

I googled some more and found part of the solution:
(it feels weird answering your own post, but hey)
The console didn't show dark grey, to fix this add "vga=791" to the Ubuntu listing of /boot/grub/menu.lst.
To change the console font you can use "consolechars -f /usr/share/consolefonts/iso01.16" or any other font to your liking in the same folder. Setting the font in /etc/console-tools/config does not seem to work (might be a known bug, need to ckeck that), but adding the above command to your ~/.bash_profile does.

Joep

---

### Post by Tuna-Fish on 2007-01-05
Does anyone know a good virtual terminal for linux where you can set the size of the screen in rows*columns and when you resize the screen (or go fullscreen) it stretches the font instead of resizing the terminal?

---

### Post by j19sch on 2007-01-07
> **Tuna-Fish said:**
> Does anyone know a good virtual terminal for linux where you can set the size of the screen in rows*columns and when you resize the screen (or go fullscreen) it stretches the font instead of resizing the terminal?
It's not exactly what you're looking for, but the two following things might be of some help.:
1) You can create another terminal profile (edit > profiles) with a bigger font.
2) You can use the zoom function (view > zoom in / zoom out / normal size).
I know these are not elegant solutions, but it's something. :) 

Regards,
Joep

---

