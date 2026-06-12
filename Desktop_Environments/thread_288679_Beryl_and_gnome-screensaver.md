---
title: "Beryl and gnome-screensaver"
date: 2006-10-30
forum: Desktop Environments
---

### Post by DemonTPx on 2006-10-30
Hi I'm using beryl 0.1.1svn, from the [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) repository, on Ubuntu Edgy.
When I start my screen saver, I get a black screen and **I don't get my window where I can enter my password anymore**. The only workaround I can use is to press ctrl-alt-F1, login and enter the command killall gnome-screensaver.
I have a Intel 945GM graphics card.

I also figured out that it just doesn't give the focus to the right window. If I had a terminal open before I start the screensaver, I can see my password inside the terminal ](*,)

edit: here's the bug report: [http://bugs.beryl-project.org/ticket/350](http://bugs.beryl-project.org/ticket/350)

---

### Post by hikaricore on 2006-11-08
You might find this useful until a better solution comes along.

[http://www.ubuntuforums.org/showthread.php?t=284804](http://www.ubuntuforums.org/showthread.php?t=284804)

It's a python script called disablegss.

The idea here is you can add beryl to the list of programs to disable gnome-screensaver while they're running.  :)

I've had similar problems with beryl and gnome-screensaver and instead of just disabling it completely, the script automaticly turns it off for me.

***extra junk removed after relizing my error***

***EDIT* Just set it to disable _beryl_ instead of beryl manager.  I kinda overlooked the obvious on this one :P *EDIT***

---

### Post by CheShA on 2007-08-20
Maybe killing beryl when the screensaver starts, then restarting it when the screensaver finished would be good for you, check [this thread]("http://ubuntuforums.org/showthread.php?p=3219643#post3219643"):

---

