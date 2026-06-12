---
title: "How do I kill the gui?"
date: 2005-10-26
forum: Desktop Environments
---

### Post by geofff on 2005-10-26
I've messed up my system so I can't log on. My intention is to start x as root user (sudo su) from console so that I can get back into the gui to undo the mistakes. However I can't kill the gui. ctl+alt+backspace only restarts it, not kills it. I've tried kill X, killall X, kill x-windows etc from init level 3 as suggested by various searches. However the gui just keeps rolling along! 

Can someone tell me what I have to kill?

(Sorry posted to the wrong forum. should have been Ubuntu. However I presume the answers will be the same!)

Thanks

---

### Post by sanjose on 2005-10-26
sudo /etc/init.d/gdm stop if you're using gnome and kdm for kde

---

### Post by geofff on 2005-10-26
Thanks sanjose - it worked.

---

### Post by HermanAB on 2005-10-26
Another way to regain control is to switch to a different pseudo terminal with Ctrl-Alt-Fn where n range from 1 to 6.  Log in as root and run init 3.

Cheers,

Herman
[http://www.aerospacesoftware.com/linuxhowtos.html](http://www.aerospacesoftware.com/linuxhowtos.html)

---

