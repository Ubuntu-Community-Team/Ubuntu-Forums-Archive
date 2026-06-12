---
title: "Beryl and Games"
date: 2007-03-17
forum: Gaming &amp; Leisure
---

### Post by PandaGoat on 2007-03-17
I have finally installed Beryl, and I am in awe, although, I would being able to play games.  Games such as Wolfentstein cannot run full screen; they become windowed.  I am also running Warcraft III TFT with wine, but after installing Beryl it is "unable to initialize OpenGL."

Specs:  Beryl/XGL and ATI Radeon 9600

Oh and dear god, is there a way to disable the shift + backspace shortcut?  It has taken me 5 hours to complete this post.

---

### Post by hikaricore on 2007-03-17
Use beryl-manager to disable beryl before playing a game.

Shortcut keys are also editable via beryl-manager /w the beryl settings manager.

---

### Post by PandaGoat on 2007-03-17
I have tried that--changing the window manager back to metacity, but with no prevail.  I am begenning to think it does more with Xgl, because before I used fglrx drivers and everything worked fine.  Is there a way to run beryl without using Xgl?

---

### Post by Mongoose on 2007-03-17
Read this to setup AIGLX with the xorg server instead:

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX)

---

### Post by Buslova on 2007-03-17
so does anyone know if AIGLX works on an ATI RADEON 9700 PRO?  I had WoW running with FGLRX before installing Beryl but now, I have no 3D acceleration.  When I get back from going out for St. Patrick's day, I'm going to uninstall Beryl & FGLRX and try this method.  if it doesn't work, i guess i'll just have to live without beryl.

Bus

---

### Post by PandaGoat on 2007-03-18
Ok, after playing around for a bit I finally understand, although, when I switch to metacity using the Beryl manager, the same thing happens because Xgl is still running.  I cannot end it lest the screen goes completely black.  I have concluded that, no matter what window manager, everything runs with Xgl when logging into Xgl session [for Beryl].  Logging in normally with no Xgl fixes all issues.

Is there a way to specify which session a program is rendered in--have beryl running [with Xgl] and opening a game in gnome-session instead. 

Note: I have both Xgl and gnome-session running so the icons and what not do not look like crap.

Code used on startup to start xgl [/usr/bin/startxgl]
```

#!/bin/sh
Xgl -fullscreen :1 -ac -br -accel glx:pbuffer -accel xv:pbuffer &
sleep 4  
export DISPLAY=:1 
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec dbus-launch --exit-with-session gnome-session

```

---

### Post by hikaricore on 2007-03-18
_**I can't verify that this will work while using special X sessions setup for ATI cards, but I can't imagine why it wouldn't.**_

Another solution you may want to look into.  Instead of wracking your brain figuring out how to disable beryl to play games, you can actually start them in a seperate Xsession instead, as pointed out here in ubuntu WoW howto: [https://help.ubuntu.com/community/WorldofWarcraft#head-5bcf9267027c1ff9001b3e20c9e3128232cd5a7d](https://help.ubuntu.com/community/WorldofWarcraft#head-5bcf9267027c1ff9001b3e20c9e3128232cd5a7d)

This can honestly be adapted for any game, and you can even use a seperate Xorg.conf file that fits the video needs of your game.  Here's my script for launching WoW:

> 
[B]cd /wow
sudo X :3 -ac _-config /etc/X11/wow.conf_ -quiet &
sleep 2[/B]
DISPLAY=:3 nvoc
**DISPLAY=:3 WINEDEBUG=fixme-all,err-all,warn+cursor,-all aoss wine WoW.exe -opengl &**
DISPLAY=:3 /root/.fluxbox/startup &

Most of the stuff in mine you can ignore, as I launch fluxbox and a script to overclock my Nvidia card.  I've highlighted the important parts with bold, and underlined the call to the specific script.

You could simply use an Xorg.conf config that you know to work with your game and name it gaming.conf and replace the directory and WoW.exe with the location and name of your game and you're good to go.  :)

---

### Post by PandaGoat on 2007-03-18
Thank you, but as usual I have errors.  I want to use my regular xorg.conf file, so I left off -config.

```

#!/bin/sh

X :3 -ac & 	
sleep 2    	

DISPLAY=:3 wine '/home/devin/.wine/drive_c/Program Files/Warcraft III/War3.exe' -opengl

```

When I run it as a normal user [in terminal], the terminal closes after a few seconds.  I tried it as root and the entire screen goes black and flashes between a grey screen with lines and the black screen until it goes to the login screen.

My Xorg.3.log is when I ran it as root because running it as a normal user failed to write one.
[Xorg.3.log]("http://pandagoat.googlepages.com/Xorg.3.log.txt")

---

### Post by hikaricore on 2007-03-18
To my knowledge, direct rendering doesn't work well in XGL.

This is why I suggested using a second xorg.conf.. if you don't wanna try it then I'm out of ideas.

---

### Post by PandaGoat on 2007-03-18
Oh, i thought it ran it with gnome-session and thus enabling direct rendering.  My mistake.  Anyway I can do something--I can log out and log in under the Gnome session.  Thank you for the knowledge :)

---

### Post by Mongoose on 2007-03-18
I still suggest tossing Xgl completely and using xorg and AIGLX.  It's the only solution as far as I'm concerned due to stability and performance issues you'll have otherwise.

---

