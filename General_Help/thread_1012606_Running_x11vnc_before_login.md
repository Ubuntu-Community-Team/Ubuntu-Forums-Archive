---
title: "Running x11vnc before login"
date: 2008-12-16
forum: General Help
---

### Post by Cool Javelin on 2008-12-16
I would like to start x11vnc before it asks for my user name and password.

Anyone know how to?

I have a script to start the x11vnc server in /usr/local/sbin.

Thanks Mark.

---

### Post by Peter09 on 2008-12-16
Unfortunately its not as easy as that, x11vnc needs an xsession running for it to work. 

To login remotely before a session is available use ssh. For a remote session with no one logged in use Freenx (which uses ssh).

[http://freenx.berlios.de/](http://freenx.berlios.de/)

---

### Post by krunge on 2008-12-16
> **Cool Javelin said:**
> I would like to start x11vnc before it asks for my user name and password.

Anyone know how to?


Hi, I posted a reply to a similar request of yours here:

[http://ubuntuforums.org/showpost.php?p=6381876&postcount=11](http://ubuntuforums.org/showpost.php?p=6381876&postcount=11)

---

### Post by bodhi.zazen on 2008-12-16
Use a different VNC server (FreeNX or vnc4server).

Personally I tunnel over ssh, so I ssh in then start the vnc server.

---

### Post by RomanIvanov on 2008-12-17
bodhi.zazen, sorry for stupid question, I am newbie in ubuntu, please post examples of how to run vncserver/client over ssh.

---

### Post by bodhi.zazen on 2008-12-17
> **RomanIvanov said:**
> bodhi.zazen, sorry for stupid question, I am newbie in ubuntu, please post examples of how to run vncserver/client over ssh.

There *was* a nice vnc over ssh ubutnu wiki page at one time , but it has been revised.

[http://martybugs.net/smoothwall/puttyvnc.cgi](http://martybugs.net/smoothwall/puttyvnc.cgi)

Here is the vnc wiki page : [https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

---

