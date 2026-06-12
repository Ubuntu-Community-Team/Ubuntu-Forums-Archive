---
title: "KTOrrent problem"
date: 2006-06-30
forum: Desktop Environments
---

### Post by raffytaffy on 2006-06-30
Every time i start ktorrent my system starts to lag..i open sys monitor and notice a gazillion kio_http instances. i included a pic of what it looks like..what can i do?  [http://img282.imageshack.us/my.php?image=screenshot15dj.png](http://img282.imageshack.us/my.php?image=screenshot15dj.png)
Also gaim cant be started..when i start it..3 instances of it pop up on sys monitor and nothing (non of my accounts log in) wtf is goin on

---

### Post by Neo Ex on 2006-06-30
I have had problems with KTorrent, too: after a while, it use a lot of CPU. I solved installing the 2.0beta version. You can download and compite it by yourself or you can use the deb package which you can find in the HOWTO section of this forum. Maybe this version can solve your problem, too.

---

### Post by Jucato on 2006-06-30
How many things are you downloading?

Usually, a kio_http exists for each single http process, like open web pages and stuff like that. It's not a problem because that's how KDE handles files and resources. But unless you are really downloading that many stuff, then it might really be a problem

---

### Post by raffytaffy on 2006-06-30
i have a 3 max limit..i have 3 runing 2 in wait:P

---

### Post by Jucato on 2006-06-30
Strange indeed. You are using the version of KTorrent from the repositories, right?

I'm not sure, but could it be possible that the reason is that KTorrent is running on GNOME? There might be a package that it needs to run efficiently, even if it isn't a dependency of KTorrent?

---

### Post by raffytaffy on 2006-06-30
i thought about that aspect...ktorrent = kde...ive decided to instal KDE desktop and run ktorrent under it..ive been meaning to do this for some time..i want more then gnome..might as well have kde...will post results once its done....and yes...from synaptic.

---

### Post by Jucato on 2006-06-30
Well, I'm running KTorrent 1.2 (the one from the Ubuntu repositories) on Kubuntu, and I can definitely say that I have not encountered this problem. In fact, I don't see any kio_http that's connected to KTorrent at all. Strange...

---

