---
title: "I tried to make Ubuntu look like a mac now it's completly unuseable!!"
date: 2009-04-26
forum: Desktop Environments
---

### Post by vinchenzosaldevar on 2009-04-26
Ahhrghhh I tried to make ubuntu look like a mac and now i think i may have killed my laptop!

I followed the instructions here [http://maketecheasier.com/turn-your-ubuntu-hardy-to-mac-osx-leopard/2008/07/23](http://maketecheasier.com/turn-your-ubuntu-hardy-to-mac-osx-leopard/2008/07/23) but unfortunatly could not get the macmenu to work 

I then  tried installing just the macmenu-applet logged out logged back in and now my pc is completly unuseable!

the pannel at the top flicks up and down every second or so, shifting all my deskdop icons down and making my whole screen oscillate giving me a headache to look at it. also It's not up for long enough for me to select any application. I can't even get to a terminal!!!

last thing i did was download macmenu-applet from... [http://rapidshare.com/files/29455993/gnome-macmenu-applet.tar.gz](http://rapidshare.com/files/29455993/gnome-macmenu-applet.tar.gz)

then entered:
tar -zxvf gnome-macmenu-applet.tar.gz
sudo  cp -f gnome-macmenu-applet /usr/lib/gnome-applets
sudo  cp -f GNOME_MacMenuApplet.server /usr/lib/bonobo/servers

logged out and now can't get anything to work.

I like to play around with my os, but i've had to wipe my hard drive and start again so many times (this will be my 3th independent install due to me unwittingly breaking things and not being able to fix them)

I really don't wanna have to wipe ubuntu again!! please please please help!!!

---

### Post by andrea000 on 2009-04-26
Just drag and drop to the themes manager.There is
some how to notes [here]("http://www.howtoforge.com/mac4lin_make_linux_look_like_a_mac")

---

### Post by UbuntuNerd on 2009-04-26
i don't know how much damage you did but you can try hiting Ctrl+Alt+f1 and drop back to the command line, log in and type this command to reinstall your desktop:
```
sudo apt-get install ubuntu-desktop
```
hit Ctrl+Alt+f7 to get back to your desktop

---

