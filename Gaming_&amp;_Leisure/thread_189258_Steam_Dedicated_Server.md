---
title: "Steam Dedicated Server"
date: 2006-06-05
forum: Gaming &amp; Leisure
---

### Post by leetcharmer on 2006-06-05
Hello, I just installed Ubuntu Server 6.06 and installed steam dedicated server and ssh on it.  The PC hosting the server was then placed in a room next to the router w/ no monitor or keyboard nearby -- so I've been using the ssh connection from other computers to gain access to mess with the server settings.  Currently, in order to start the steam server -- I've needed to login via ssh and start it manually from there, is it possible to somehow start it remotely, and then logout of my ssh connection while still having the server run?

---

### Post by frying_fish on 2006-06-05
if you have screen installed then you can run it behind a screen, or you can set up a service if it can run in a daemon mode.

If it can't be run as daemon, then install screen, and login, then type "screen" and hit enter, then you can run your server, and to logout whilst it still runs hit ctrl+a , ctrl+d and it will "disconnect" that screen, taking you back to your original shell, from there you can logout normally. To "reconnect" to the screen type screen -r , from any shell (as the same user) and it will reconnect to that session for you to alter things.

---

### Post by leetcharmer on 2006-06-05
awesome, thanks!

---

