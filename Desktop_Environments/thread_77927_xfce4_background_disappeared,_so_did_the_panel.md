---
title: "xfce4 background disappeared, so did the panel"
date: 2005-10-17
forum: Desktop Environments
---

### Post by AlexMartinius on 2005-10-17
Good evening all.

I installed Ubuntu 5.10 on my server, but since my other pc broke down yesterday, I use it for other purposes too. But using Gnome was quiet frustrating on a older pc (PIII 500 mhz, 384 MB RAM), so ubuntu_demon suggested I tried xfce.

It was working fine, a bit smoother than Gnome too. So no problems. That all changed when I tried to get my display set to 1280x1024. That finally worked (dpkg-reconfigure xserver-xorg), but my desktop background  picture was gone. It became brown, instead of [this](http://martinius.mine.nu/desktop.jpg).

I tried to set it to the picture again, but the settings were still right. I tried logging in again, but still just the brown background. Someone suggested to kill bonobo-activation-server, but the process kept starting again, and nothing happened to my background. And then all went wrong. 

I couldn't open the system monitor anymore. As I tried to log out, it wouldn't log me out. The taskbar was still there, the panel wasn't. I went to a terminal with ctrl+alt+f1 and rebooted te computer (probably not the best thing to do, but I didn't know what else to do, I'm not very good with Linux). After rebooting I started xfce again, but except for the taskbar, nothing appeared on my screen.

Even after uninstalling (debfoster -f, xfce was the only thing I installed since I last updated the keepers file) and re-installing xfce, I still only get the taskbar and a brown desktopbackground.

I obviously messed up something (or some things), but I have no idea what it was this time. So ubuntu_demon suggested I started a threat here. Perhaps someone can help me, I would like xfce to function normally again.

If more information is needed, just say so. I got no idea what could be relevant.

---

### Post by oghanchi on 2005-10-17
I think you need to do the following two steps:

1- run from terminal --->  killall nautilus
2- run 'xfdesktop' from a terminal or via menu->run dialog.

---

### Post by AlexMartinius on 2005-10-17
[QUOTE=oghanchi]I think you need to do the following two steps:

1- run from terminal --->  killall nautilus
2- run 'xfdesktop' from a terminal or via menu->run dialog.[/QUOTE]
When I go into a terminal with ctrl+alt+F1, I can run killall nautilus. But I can't run xfdesktop, "(xfdesktop:8424): gtk-WARNING **: cannot open display:".

---

### Post by ubuntu_demon on 2005-10-18
Do the following :

```

$ ps aux | grep xfdesktop

```

to see whether xfdesktop is running or not. 

If it is running you should see something like this :
> 
$ ps aux | grep xfdesktop
username     5690  0.0  1.4  13184  7424 ?        S    Oct16   0:14 xfdesktop
username    31805  0.0  0.1   2984   712 pts/0    D+   10:22   0:00 grep xfdesktop


I suspect it is running. If it is indeed running then do the following :

```

$ xfdesktop -reload

```

because :
> 
       -reload
              Causes  an  already-running  instance of xfdesktop to reload all
              its settings, including loading a new random backdrop if using a
              backdrop list.


If this doesn't solve your problem then please give us your ~/.xsession-errors

---

### Post by AlexMartinius on 2005-10-18
xfdesktop is not running.

---

### Post by AlexMartinius on 2005-10-18
[My .xsession-errors.](http://martinius.mine.nu/xsession)

---

### Post by No6 on 2005-10-18
Don't run the command from the CTRL-ALT-F1 terminal. Open up a terminal session in the gui. (you may need to use ALT-F2 to get a run box if your panel has gone.)

Don't forget to save your session when you log out or nautilus will take over again.

---

### Post by ubuntu_demon on 2005-10-18
and the next time you start nautilus in xfce4 make sure it runs like this :
nautilus --no-desktop

---

### Post by AlexMartinius on 2005-10-18
It's working again!

Ik logged in to xfce4 again, killed nautilus from the terminal and started xfdesktop using alt+F2 and then started xfce4-panel, also using alt+F2. Now I can see the background picture again and the panel.

Thanks to all for helping.

Just one other question about ubuntu_demon's last post. I don't start nautilus manually, I don't know why it's loaded, so how can I make sure it loads with nautilus --no-desktop?

---

### Post by No6 on 2005-10-18
[quote=AlexMartinius]It's working again!
Just one other question about ubuntu_demon's last post. I don't start nautilus manually, I don't know why it's loaded, so how can I make sure it loads with nautilus --no-desktop?[/quote] 
Try this in a terminal it should do the trick...

```
gconftool-2 -s /apps/nautilus/preferences/show_desktop -t bool false

```

---

### Post by ubuntu_demon on 2005-10-18
[QUOTE=No6]Try this in a terminal it should do the trick...

```
gconftool-2 -s /apps/nautilus/preferences/show_desktop -t bool false

```[/QUOTE]
but if you do it this way you probably won't have a desktop in gnome :)

---

### Post by AlexMartinius on 2005-10-18
It would be nice to still be able to work in Gnome. I guess.

Acutally it won't matter that much. I'll be doing most of the stuff on the server in SSH again, since my other pc works again, I installed a new PSU today.

Perhaps I'll use xfce4 when I login with VNC. I haven't figured that out yet.

---

### Post by ubuntu_demon on 2005-10-18
[QUOTE=AlexMartinius]It would be nice to still be able to work in Gnome. I guess.

Acutally it won't matter that much. I'll be doing most of the stuff on the server in SSH again, since my other pc works again, I installed a new PSU today.

Perhaps I'll use xfce4 when I login with VNC. I haven't figured that out yet.[/QUOTE]
You have to edit your /etc/vnc.conf. This is the relevant part :

```

# $vncStartup points to a script that will be started at the very beginning.
# $vncStartup = "/etc/X11/Xsession";
$vncStartup = "/usr/bin/startxfce4";

```

---

### Post by AlexMartinius on 2005-10-18
[QUOTE=ubuntu_demon]You have to edit your /etc/vnc.conf. This is the relevant part :

```

# $vncStartup points to a script that will be started at the very beginning.
# $vncStartup = "/etc/X11/Xsession";
$vncStartup = "/usr/bin/startxfce4";

```[/QUOTE]
Thanks. I've been searching the web for this, but couldn't find anything. Well, I did find some stuff, but thought that it could be done much easier. You just proved I was right about that. ;)

---

