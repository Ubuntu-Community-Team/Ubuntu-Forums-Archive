---
title: "Connecting to working remote x-session"
date: 2009-07-12
forum: Desktop Environments
---

### Post by j_kubik on 2009-07-12
Hello,

Does anybody know if it's possible to remotely attach to working x-session? I can create remote x-session conection to another (k)ubuntu machine, but I am creating completely new kde/gnome process. I am using that feature to help my friends with some computer problems. Now I am trying to get it working like that: instead of connecting and starting new gnome/kde, i want to connect to their working x-session, so they see what i'm doing, and so i can show them how to do things. I know that there are some programs (like vnc servers, etc.) that probably would do the trick, but i want to know if this is possible using only Xorg and kde/gnome, and possibly some conf-files editing.

j_kubik

---

### Post by Zorael on 2009-07-13
Kubuntu comes with Krfb (remote desktop sharing), but it's broken and you don't want to use it ever.

I'd suggest you install the **x11vnc** package; that should net you both a viewer and a server, though there certainly are more visually appealing viewers. You'd need to do some minor terminal-fu to configure it, though. This'll just get you started, there's a [whole slew of configuration options](http://linux.die.net/man/1/x11vnc) you can peruse at leisure afterwards.

Enter the following in a terminal on the host machine and pick a password.
```
$ x11vnc -storepasswd
```

Then create a script (still on the host machine) in your text editor of choice (Kate, kwrite, nano, ...) containing the following.
```
#!/bin/bash

x11vnc -rfbauth ~/.vnc/passwd -bg **-rfbport 5900** -forever
```
Save it someplace and make it executable, either by right-clicking it in Dolphin (permissions -> set as executable), or in a terminal with **chmod +x *<filename>***. (Or chmod 755 filename, or whatnot.) If you don't have the **-rfbport 5900** argument it won't connect to the currently running session, instead likely creating a new one, such as it would if you were to switch user on the host machine itself.

Then run it. If you run it in a terminal it'll spout some info about how it's starting the server, and any error messages will be output to there.

You can set it up to start a tray icon (and a butt ugly GUI) if you modify the script to say this instead.
```
#!/bin/bash

x11vnc -rfbauth ~/.vnc/passwd -bg -rfbport 5900 -forever **-gui -tray=minimal,iconfont=14x17**
```
The obvious advantage being that you can close the server easily, graphically. If you use the first script, run **killall x11vnc** in a run box (alt+f2) or in a terminal to terminate it.

If you add **-avahi** to the command, it'll broadcast that the service is available to other machines in the network that are Avahi/Bonjour/Zeroconf-aware. In KDE, it would (for instance) show up in Dolphin, if you go to Network -> Network Services, or if you enter the location '**zeroconf:/'**.

If you add **-ssl**, it should encrypt stuff if you have the necessary packages installed. And there's just a huge number of other arguments to configure ssl, but if it's in a local network you probably needn't bother.

---

