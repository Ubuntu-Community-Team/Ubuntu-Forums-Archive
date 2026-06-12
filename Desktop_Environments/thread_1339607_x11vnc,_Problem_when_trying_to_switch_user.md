---
title: "x11vnc, Problem when trying to switch user"
date: 2009-11-27
forum: Desktop Environments
---

### Post by mindmachine on 2009-11-27
Good evening altogether (or whatever, depends where you live ;)).

Now, I`ve got some kind of tricky little problem.

I`m running x11vnc successfully on my Ubuntu 8.04 (Gnome) and I'm able to establish a connection via ssh (by -localhost) from wherever (LAN/WAN) to my login screen, I can login to my desktop without any problems (using TightVNCviewer). 
Now, when I logoff, the remote desktop shuts down, but I can easily reconnect to Login Screen again. But when I try to switch user, the display breaks down and becomes almost unreadable. Nevertheless, I'm still able to use my mouse and enter the password for the other user even if I can't see the desktop (or login) environment properly.
And it gets even better. When I logoff the other user (by guessing where to tab with my mouse :D) and reconnect to my first user, the screen is usable and stable again.
Btw this affects both, local and remote screen. 

Now when I close the session at this point, before I connect to my first user, I'm not able to reconnect anymore as I get a "wrong passwd" message by TightVNCViewer. Cancelling and restarting the ssh connection doesn't work, restarting GDM doesn't work, restarting x11vnc doesn't work and doing this in various combinations also doesn't :-|... Only way to get the server back on is a reboot (and even this led in one case to a "hung up" but I'm not sure if this happened just by accident...)

I'm using this command to start x11vnc (registered in rcS.d):
> sudo x11vnc -noxdamage -forever -shared -localhost -bg -rfbauth /home/christian/.vnc/passwd -auth /var/lib/gdm/:0.Xauth -display :0 -o /var/log/x11vnc.log
(i know, the sudo is most likely not necessary but it works, so why change it??)

And this one in /etc/gdm/Init/default:
> /usr/bin/x11vnc -noxdamage -forever -shared -localhost -bg -rfbauth /home/christian/.vnc/passwd -o /var/log/x11vnc.log
I know, the sudo command is most likely not necessary but it works, so why change it?

The value KillInitClients in gdm.conf-custom is also set to false.

Logs don't show any interesting information. Is this a magic cookie problem? If yes, is there a possible solution? 

(Why do I need this problem solved anyway? --> My wife works on this machine and today she ordered some stuff via internet and had almost finished when I tried to login, got a black screen, some flickers, didn't notice my wife and did some /etc/init.d/gdm restart :-\"... So it would be nice to recieve any comments, "brain burps", thoughts, might-be's or whatever to avoid the usually "/gdm restart" following loud phonecall to my office...)

Thank you for reading and if you need some deeper explanation or any logs, just shout... (hoping that still someone uses Hardy...)

mindmachine

---

