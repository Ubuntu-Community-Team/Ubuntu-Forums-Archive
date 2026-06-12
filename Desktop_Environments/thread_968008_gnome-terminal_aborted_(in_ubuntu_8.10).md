---
title: "gnome-terminal aborted (in ubuntu 8.10)"
date: 2008-11-02
forum: Desktop Environments
---

### Post by imperialline on 2008-11-02
Since upgrading to Ubuntu 8.10, I am unable to start gnome-terminal from my local PC display (via Cygwin X or XWIN32 server) to a headless Ubuntu 8.10 server.

Basically, gnome-terminal does a fatal exit with the following error message:

**
ERROR:terminal-app.c:1525:terminal_app_init: assertion failed: (app->default_profile_id != NULL)
Aborted


Has anyone seen the same problem and what can be done about it?

Please note that other terminal apps such as xterm, uxterm, xfce4-terminal, powershell, etc. work fine and I can even run update-manager, synaptic remotely. It is just gnome-terminal that does not like to start.

---

### Post by imperialline on 2008-11-02
I am really surprised that nobody sees this issue or perhaps nobody really uses X11 to log in the system remotely?

---

### Post by atroxes on 2008-11-03
I do (did rofl) use X11. Now it's broken when trying to boot headless. Was awesome to have auto-login enabled and just being able to use vino with no hastle what so ever.

---

### Post by sophitialer on 2008-11-03
[img]http://www.top1gaming.com/cosplay/shaiya-1.jpg[/img]See more pics [[color=#800080]click here[/color]](http://www.top1gaming.com/coscontent-153.html).  Want to see more [[color=#800080]cosplayer[/color]](http://www.top1gaming.com/cosplayer.php) ? Show yourself on our forum [[color=#800080]click here [/color]](http://www.top1gaming.com/forum/forumdisplay.php?fid=29).**Recommend : **[[color=#0000ff]Fate Stay Night cosplay [/color]](http://www.top1gaming.com/coscontent-83-8.html)   [[color=#0000ff]Chobits cosplay[/color]](http://www.top1gaming.com/coscontent-46.html)

---

### Post by dsplabs on 2008-11-04
> **imperialline said:**
> 
Basically, gnome-terminal does a fatal exit with the following error message:

**
ERROR:terminal-app.c:1525:terminal_app_init: assertion failed: (app->default_profile_id != NULL)
Aborted


I have the same issue when i start gnome-terminal.

---

### Post by imperialline on 2008-11-05
I think a bug report needs to be submitted. Funny that nobody saw this problem during the beta testing period.

---

### Post by unc0nn3ct3d on 2008-11-08
I'll chime in on this as well.. The weird thing is that I have had no problems up until now.. Infact I have 3 term windows open right now but when I try to start another this is the error I receive

ERROR:terminal-app.c:1525:terminal_app_init: assertion failed: (app->default_profile_id != NULL)
Aborted

---

### Post by fofftorrent on 2008-11-15
how can one submit a bug report?

---

### Post by fofftorrent on 2008-11-15
please submit further details to the bug report

[https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/298426](https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/298426)

---

### Post by giacomo.c on 2008-11-15
i had this problem aswell...

i used fluxbox with the gnome-terminal as my default terminal, but after the "upgrade" gnome broke entirely... i couldn't log in with the gnome sessions without getting a bunch of errors.

long story short, debian is working much better.\\:D/

---

### Post by monkeyking on 2009-02-25
I have been experiencing this one also once in a while,
it's highly annoying.
But it seems to be fixed in future versions.

[https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/298426](https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/298426)

---

