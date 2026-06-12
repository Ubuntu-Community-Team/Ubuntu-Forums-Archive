---
title: "opening tools and and other stuff through ssh"
date: 2007-12-03
forum: Desktop Environments
---

### Post by linuxsux on 2007-12-03
i have this big server at my workplace and i am the admin and i was wondering how do you ssh into someones elses computer and open up something like firefox. i know how to kill a program through top. Also one of my coworkers turned off ssh and we need to get it back on how do you do that

---

### Post by Aseld on 2007-12-03
Well, to SSH:

```
ssh [IP address]
```

You won't be able to use Firefox though, as it's a graphical program. If you want graphics maybe try something like VNC.

How did they turn SSH off? Did they just stop the service? If so,

```
sudo /etc/init.d/ssh restart
```

If they've uninstalled it:

```
sudo apt-get install ssh-server
```

---

### Post by linuxsux on 2007-12-04
they blocked it and also how do i use vnc to open up firefox is there a tutorial

---

### Post by Aseld on 2007-12-04
Well, install VNC, connect and click on the Firefox icon. There will be tutorials on the Web, I'm sure.

---

### Post by mellowd on 2007-12-04
SSH is all terminal, so VNC would be your next bet

---

### Post by linuxsux on 2007-12-07
i installed vnc client but i don't know how to use it

---

### Post by bukwirm on 2007-12-07
You could also use ssh with [X forwarding]("http://www.ssh.com/support/documentation/online/ssh/adminguide/32/X11_Forwarding.html").

---

### Post by Rick Z on 2007-12-07
you may want to look into webmin.  You can setup to your co-worker's workstation and administrate through https.  once you are setup as root of webmin.  you can virtually doing a lot of stuff.  you can even login ssh from webmin.  You may even view entire / (root) directory.  too many feature to describe here.

---

