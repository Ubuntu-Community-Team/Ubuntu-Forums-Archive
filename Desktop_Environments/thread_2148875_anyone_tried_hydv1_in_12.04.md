---
title: "anyone tried hydv1 in 12.04?"
date: 2013-05-27
forum: Desktop Environments
---

### Post by malspa on 2013-05-27
I saw this article for installing HY-D-V1 (the desktop from Hybryde Linux or Hybryde Fusion) in Ubuntu 13.04: [http://www.linuxbsdos.com/2013/05/22/install-hy-d-v1-desktop-on-ubuntu-13-04/](http://www.linuxbsdos.com/2013/05/22/install-hy-d-v1-desktop-on-ubuntu-13-04/)

It's also supposed to work in 12.04, which I'm running, but it crashes right away each time I log into it. To install it, I used this to add the PPA:

```
$ sudo add-apt-repository ppa:olivelinux36/hydv1-desktop-dev-precise
```

Anybody had any success running HY-D-V1 in 12.04?

---

### Post by Eustass on 2013-06-14
I ran into the same problem, I haven't tried it with Ubuntu 13.04 yet but I don't want to since I already installed Hybryde on my laptop. Works well. 
Live version was glitchy but once installed it worked good. As far as HY-D-V1, it is a nice concept and I'm only using Hybryde because of the HY-D-V1 desktop.
It looks really neat, and I hope there is a fix for people wanting it to install it on their ubuntu os.

---

### Post by malspa on 2013-06-15
Sent an email to the project's developer; he replied and suggested that I examine the results of the following:

```
steve[~/Desktop]$ cd /usr/share/hydv1/
steve[/usr/share/hydv1]$ ./hydv
```

In my case, HY-D-V1 was crashing because of Wally wallpaper changer, which was installed here. But I've been using Wallch instead, so I removed Wally, and that solved the problem -- HY-D-V1 is running fine in 12.04 now.

---

