---
title: "System &gt; admin &gt; anything there isn't working"
date: 2006-03-31
forum: Desktop Environments
---

### Post by majicaldutch on 2006-03-31
I'm pretty sure i have administrative abilities, i just install ubuntu tonight, but did not get my wireless working during the install. Now anything I select in the System > Administration Menu doesnt load. It asks for my password, and then says starting program for a while, and the wheel spins, but the file eventually just dissapears and ceases loading, nothing pops up.

---

### Post by towsonu2003 on 2006-03-31
what happens when you do (from a terminal) ```
sudo gedit file
```

error messages? if so, please copy paste here. or does the text editor launch? if it launches, close without saving the file and try ```
sudo synaptic
``` and copy paste error messages if it crashes (doesn't launch).

PS. You will write your own password on "Password:" prompt.

---

### Post by majicaldutch on 2006-03-31
Hey just saw your post, if you get this my aim is the same as this username, im trying to do what you said right now but im not even really sure how to open the prompt yet,

---

### Post by majicaldutch on 2006-03-31
got the root user mesage on second try. but im very confused then

---

### Post by xenmax on 2006-03-31
This might help:
[http://www.ubuntuforums.org/showthread.php?t=146859](http://www.ubuntuforums.org/showthread.php?t=146859)

---

### Post by majicaldutch on 2006-03-31
I tried everything that thread says, no help. I even checked the file /vars/log/install/cdebconf/questions.dat to look at what I told the computer. it registers that for username root, i have a password. and that for username alastaire i also have a password. the alastaire account has been the one i've been logging in with. but i cant log in with the username root and the password i have assigned it.

---

### Post by xenmax on 2006-03-31
> but i cant log in with the username root and the password i have assigned it.
If by this, you meant that you tried to login as root at start-up, then its ok because AFAIK in Ubuntu, root login is disabled by default.
If you are trying to follow instructions in thread which said login as root, then like it says, open a terminal and type
```
su root
``` followed by root password

---

### Post by majicaldutch on 2006-03-31
Cool, got that working. Now my wireless card isn't. :(
thanks for your help.

---

