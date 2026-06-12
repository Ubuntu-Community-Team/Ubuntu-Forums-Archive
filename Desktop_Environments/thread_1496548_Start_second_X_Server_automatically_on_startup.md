---
title: "Start second X Server automatically on startup"
date: 2010-05-29
forum: Desktop Environments
---

### Post by JohannesD on 2010-05-29
Hi!
I want to use my additional graphics card to display a second X-Server on my TV screen. When starting the computer, I want a specific user to be logged in automatically, while on the PC screen gdm is running as normal.

Both graphics cards are installed properly, I created two X-Server layouts in xorg.conf that also work. I only have problems with starting two x servers.

Ok, that's what I have done so far: I logged in and typed the following in a console:

```
sudo /usr/bin/X -layout TVLayout vt7 :1
```

I a second console, I typed:

```
sudo gnome-session --display :1
```

This will start both X-Server and Gnome on my TV. Unfortunately, the User to be logged in is root. That is of course not what I want. But the more important problem for me seems to be doing the above things automatically at startup.

I tried creating two init.d scripts that start X and gnome, but it didn't work (nothing happens). I think this is because I haven't found a way to ensure that gnome is started not until X is running.

I've found out that startx offers this, but I don't know how to use it. When I type

```
sudo startx -- -layout TVLayout vt7 :1
```

a second X server is started on the TV, but no Gnome is displayed. Instead, the panels on the desktop change as if root was logged in, but the desktop icons stay the same. So I think the gnome-session is started not on the new X server instance but on the old one. Where can I specify this? And where can I define, which user will be logged in?

Can someone help? 

Thx,
Johannes

---

