---
title: "Desktop Drape, on 10.04, Broken?"
date: 2010-06-21
forum: Desktop Environments
---

### Post by ffixcollector on 2010-06-21
I have installed drapes and made sure that there is a startup entry for drapes on my new 10.04 system. 
Desktop drapes will not automatically run after the computer is started. 

What can I do to fix this?

---

### Post by MasterShihoChief on 2010-06-25
Yes, it seems its broken. It was working for a a month or so when it came out, but it seems updates have completely broken it. It will start but when trying to switch it does nothing, when going into preferences, it opens normally and then after being in it for more than 15 seconds the whole thing crashes. Other than that the process mono comes up once or twice in the process manager and eats 200% processor power and crashes the system. Hope it gets fixed soon as i grow tired of changing the background every day.

---

### Post by Warren North on 2010-06-25
Really like Desktop Drapes, I glad it works with 10.04 a little.
I could not get it to work with Hardy.
This program was a great idea. I love this kind of stuff.

---

### Post by ffixcollector on 2010-12-31
> Bob-El

Well, I got it working. Here’s the deal…
There’s a folder in the Home directory called .config and in it is a folder called “autostart”. In “autostart” is a file called “drapes.desktop”. Opening it with gedit reveals:

[Desktop Entry]
Type=Application
Name=Drapes
Encoding=UTF-8
Version=1.0
Exec=bash -c “sleep 10; drapes”
X-GNOME-Autostart-enabled=true
Comment[en_US]=Desktop wallpaper changer
Comment=Desktop wallpaper changer

The problem with my file is that “Type=Application” was missing. Obviously a bug in Ubuntu. I entered that line and added the “sleep 10&#8243; line in “Exec=”, rebooted and, voila! drapes loaded.

I thought you’d like to know and perhaps if anyone else mentions the same problem, you can tell them how to fix it. :)


From: <http://ubuntugenius.wordpress.com/2009/08/26/automatic-wallpaper-changer-for-ubuntu/>

---

