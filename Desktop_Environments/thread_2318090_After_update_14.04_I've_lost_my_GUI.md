---
title: "After update 14.04 I've lost my GUI"
date: 2016-03-23
forum: Desktop Environments
---

### Post by NMbottlecap on 2016-03-23
I'm at my wits end here. I did an update over the weekend and on reboot I just got a KUBUNTU splash screen with no login.  I tried an older kernel 3.19.0-56, and I'm able to get a terminal login.  I've tried restarting, I've tried different virtual consoles, the only note there is tty7 doesn't provide a login.  If I try "$sudo startx" or "$startx" I get the following

 xauth: timeout in locking authority file /home/$USER/.Xauthority <which I made a backup of and then deleted.

 then 

 /etc/X11/xinit/xserverrc: 3: exec: /usr/bin/X: not found 

then 

xinit: giving up
xinit: unable to connect to the X server: Connection refused
xinit: server error
xauth: timeout in locking the authority file /home/$USER/.Xauthority

Also I just tried to install ssh and I got a very telling error from apt-get.  It's 115 lines long so I put it in a pastebin: [http://pastebin.com/PKbt2W9U](http://pastebin.com/PKbt2W9U)
The only other thing of note, is I've gone from a dual head desktop to a single.  My video card is a Nvidia GTX750ti.

Please help, I don't want to reinstall.

---

### Post by v3.xx on 2016-03-24
Sounds like .Xauthority either needs to be reset or a permissions problem has been created.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=.Xauthority&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=.Xauthority&sa=Search&cof=FORID:9)

---

