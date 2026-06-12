---
title: "Running game in it's own Xserver"
date: 2005-07-27
forum: Gaming &amp; Leisure
---

### Post by KRavEN on 2005-07-27
Anyone know how I can get this done under ubuntu?  I've found a couple of scripts that will launch the game in it's own xserver instance when you fire it off but I'm having a permissions problem.  I found the gentoo guide that talks about this and I set the permissions for display :1 using xauth but I still get the:

```
kraven@p4:~$ X :1
X: user not authorized to run the X server, aborting.

```
I can sudo start the :1, but if I launch the game on that server it immediatly crashes.

xauth looks like this:

```
kraven@p4:~$ xauth
Using authority file /home/kraven/.Xauthority
xauth> list
p4/unix:1  MIT-MAGIC-COOKIE-1  9737c9d384f66e732d90dd221c9bd81a
p4/unix:0  MIT-MAGIC-COOKIE-1  9737c9d384f66e732d90dd221c9bd81a
localhost.localdomain/unix:0  MIT-MAGIC-COOKIE-1  9737c9d384f66e732d90dd221c9bd81a
localhost.localdomain/unix:1  MIT-MAGIC-COOKIE-1  9737c9d384f66e732d90dd221c9bd81a
```

What am I missing?

---

### Post by KRavEN on 2005-07-28
Am I really the only one wanting to do this or am I asking a stupid question?

---

### Post by KRavEN on 2005-07-29
[QUOTE=KRavEN]Am I really the only one wanting to do this or am I asking a stupid question?[/QUOTE]
 ahh, found it by searching for xauth:

[http://ubuntuforums.org/showthread.php?t=51486&highlight=xauth](http://ubuntuforums.org/showthread.php?t=51486&highlight=xauth)

---

