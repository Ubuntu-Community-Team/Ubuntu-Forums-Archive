---
title: "How to change resolution in xfce"
date: 2005-08-08
forum: Desktop Environments
---

### Post by served on 2005-08-08
i just cant use xfce bcs its killing my eyes, need a little help.
How can i change resolution in xfce4? i cant find the place where to change it!

---

### Post by blind0wl on 2005-08-09
Dont know much about xfce, but try running xfce-mcs-manager from a console

---

### Post by served on 2005-08-09
root@****:~ $ xfce-mcs-manager

** (xfce-mcs-manager:4032): WARNING **: Multi channel MCS manager already detected for screen 0

id like to switch pixel rate to 1024x.... but i have some kind 1600x... Like very small letters and veri sharp but small.

---

### Post by TestDummy! on 2005-08-09
[QUOTE=served]root@****:~ $ xfce-mcs-manager

** (xfce-mcs-manager:4032): WARNING **: Multi channel MCS manager already detected for screen 0

id like to switch pixel rate to 1024x.... but i have some kind 1600x... Like very small letters and veri sharp but small.[/QUOTE]
 What about...

right click > Settings > Display Settings 

(If I remember right) 

You should be able to switch to it from there.

---

### Post by mctavish on 2005-08-09
I have a poor memory, so I hope I get this right. 

I had problems at first getting a decent screen res with xfce4. No matter what I chose through the xfce4 settings gui, I'd get the same big dumb resolution.

I eventually found a particular X config file was forcing this res. 

The file is (IIRC!!!) /etc/X11/xinit/xserverrc 

The line in this file read
exec /usr/bin/X11/X -dpi 100 -nolisten tcp

I  took out the "-dpi 100" bit and lo! I could change my display settings. A great relief it was.

Now I have no idea why I didn't read of anyone else having this problem. It may have only hit me because I did a server install and then installed xfce4 on top of that. Who knows.

You should try the gui first of course - that is more likely your answer. 

Nonetheless this is a good opportunity for me to document my woes for the possible benefit of others.  

:)

---

### Post by served on 2005-08-13
root@****:~ # /etc/X11/xinit/xserverrc

Fatal server error:
Server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again.


When reporting a problem related to a server crash, please send
the full server output, not just the last messages.
Please report problems to [email]debian-x@lists.debian.org[/email].



This is what i get.

and i dont have a place where i can change it.

---

### Post by mctavish on 2005-08-14
Actually I meant to try to edit this file, rather than entering that line on the command line.

But forget my advice anyway. I read the thread properly this time and noticed your second post where you said your resolution was very high - with very small letters. What I was getting was a very low resolution - ie big letters.

So I'm sorry I can't help.

Did you try what testdummy suggested by going 

right click > Settings > Display Settings ?

---

### Post by served on 2005-08-14
right click > Settings > Display Settings

i dont have that display settings change. there are "All Settings..." and "Backdrop..."

---

