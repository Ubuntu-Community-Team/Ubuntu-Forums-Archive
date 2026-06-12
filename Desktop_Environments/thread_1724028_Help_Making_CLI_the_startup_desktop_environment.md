---
title: "Help: Making CLI the startup desktop environment"
date: 2011-04-07
forum: Desktop Environments
---

### Post by TheBane on 2011-04-07
I have 8.04 on my iMac G3 PowerPC (running beautifully), and I was just wondering, as Google has failed me, is there anyway to make the CLI the environment that boots, before Gnome? Basically I want to, instead of having it boot right into Gnome, boot into a login prompt. Then I can 

```
startx
```when I actually **need** Gnome. I really only use gnome when I want to watch videos and such. Everything else I use the shell for. 

Any thoughts?

Many thanx in advance sirs and ma'ams... :) Much love to my Ubuntu community.):P

---

### Post by sisco311 on 2011-04-07
Hi,

To disable GDM just run:
```
sudo update-rc.d -f gdm remove
```

To (re)enable it:
```
sudo update-rc.d -f gdm defaults
```

But you don't need an X server to watch videos. Just change the resolution of the virtual consoles:
[https://help.ubuntu.com/community/ConsoleFramebuffer](https://help.ubuntu.com/community/ConsoleFramebuffer)

and use mplayer or vlc:
[http://ubuntuforums.org/showthread.php?t=882596](http://ubuntuforums.org/showthread.php?t=882596)

---

### Post by TheBane on 2011-04-07
Many thanks sir! 

[IMG]http://whosawesome.com/images/awesome.jpg[/IMG]

---

