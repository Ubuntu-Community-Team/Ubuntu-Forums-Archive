---
title: "a question about wallpaper inbetween KDM and KDE desktop during Ksplash"
date: 2008-01-13
forum: Desktop Environments
---

### Post by DigitalDuality on 2008-01-13
I'm trying to create a pretty cohesive theme on this machine and i don't get it.

I have a KDM theme.. it loads properly, i log in, my ksplash comes up.. but the background (not of ksplash itself) is a default blue color. And then KDE pops up with my wallpaper of choice.

How do i change the color of the background/wallpaper as Ksplash is displaying?

I've done this before but no idea how i did it. And it's not always just a default color.. (speaking my memory here, not recently). I've seen old wallpapers show up during this window of time i'm speaking up during the DE boot process.

anyone have any ideas?

---

### Post by DigitalDuality on 2008-01-13
I guess that's a no.

---

### Post by TeaSwigger on 2008-01-14
Hello, I just saw your post. It can take persistance around here. I found that out the hard way!

Just like you, I had actually fussed with all that a while ago and frankly forget a load of it. However, poking around the settings here, I think what I'd try is:

System Settings > Advanced > Login Manager

or just run

kdesu kdm

or is it...

kdesu kdmtheme

? lol anyway, once there, under Background, try setting the wallpaper and colors to match the login & splash. Hopefully that works, let me know.

---

### Post by DigitalDuality on 2008-01-14
hey :) thanks for the reply.

Unfortunately that doesn't do the trick.

---

### Post by DigitalDuality on 2008-01-14
apologies, upon reboot, rather than just a restart of X... it took.  Thanks a ton :)

Edit: Nevermind, rebooted again and it's back to the way it was.

---

### Post by Brad_au on 2008-07-02
I spent ages trying to work this out too.

The way I got it to work was:

System Settings > Advanced > Login manager -to change the login background

System Settings > Desktop -for the desktop

The hard part to find out was to change the file:
/usr/share/apps/ksplash/Themes/kubuntu/Background.jpg -this is the background during the splash screen. The Readme in the same directory gives instructions.

Hope this helps someone.

---

