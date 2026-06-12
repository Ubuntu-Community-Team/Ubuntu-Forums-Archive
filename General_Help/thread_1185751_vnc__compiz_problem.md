---
title: "vnc / compiz problem"
date: 2009-06-12
forum: General Help
---

### Post by dersu on 2009-06-12
Hello,
I am running ubuntu 9.04 64bit.
At work, unfortunately I have to use an xp.
I want to control my ubuntu from xp.
So I use VNC.
I can connect to my Ubuntu but I can't control it. I have just the view.
After I have read some forums here, I want to try to disable compiz, I think it may be the solution for me.
But how can I do this from my work. 
I can make an ssh connection.
So how I can kill gdm which is running at tty7, disable compiz at the cli, or maybe disable directly compiz without to log out from gui? 
Thank you very much.

---

### Post by dersu on 2009-06-12
okay,
I did :

sudo /etc/init.d/gdm stop
pkill compiz.real

but now I can't start again the gui,
startx or sudo startx doesn't succeed.

please help.

---

