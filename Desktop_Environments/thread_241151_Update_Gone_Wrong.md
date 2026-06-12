---
title: "Update Gone Wrong"
date: 2006-08-21
forum: Desktop Environments
---

### Post by penguinchrissy on 2006-08-21
I just installed ubuntu  and I ran the update, the when I restart I get and x-config isn't configered right or something of the sourghts. I'm sure this is somewhere in the fourms but I can't find it and I don't know what to look for. If you can help or point me in the right direction I appricate very much.

---

### Post by meng on 2006-08-21
Try
sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10
then
startx

---

### Post by backdoc on 2006-08-21
I had the same problem.  

[INDENT][http://ubuntuforums.org/showthread.php?t=230945]("http://ubuntuforums.org/showthread.php?t=230945")[/INDENT]

The things in that thread worked "fair".  I ended up uninstalling all of the Xgl stuff and just live with regular X.  

I didn't have the problems in xfce4, because it just used the regular X server, I guess.  You might be able to just start up using "startx" or "startxfce4".

---

