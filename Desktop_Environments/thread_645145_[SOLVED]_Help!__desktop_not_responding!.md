---
title: "[SOLVED] Help!  desktop not responding!"
date: 2007-12-19
forum: Desktop Environments
---

### Post by rob1984 on 2007-12-19
help!  

my "desktop" has stopped working.

i'm using gnome on gutsy
all my desktop icons have disappeared and the whole desktop doesnt respond to anything eg.  right clicks, dragging a box..
both pannels are working fine
i havent messed aroung with any settings

can anyone help???

---

### Post by benerivo on 2007-12-19
It sounds like a problem with your user profile rather than a system wide problem. Try making a new user account and logging in to the new one, to see if that has any effect.

---

### Post by rob1984 on 2007-12-19
ok, but now i can't even log in. after i type my username and password i get a blank screen.

i havent set up a root login, so can you tell me how to create a new account, maybe from the CLI?  

i'm having to use my windows partition for this so i may take a while between posts.

cheers

---

### Post by benerivo on 2007-12-20
So you made that new account and now you are reaching the graphical gnome login screen, where you try to log in and it takes you to a completely blank screen on either login. Is this right?

To create a new user from the CLI, use the following command...```
sudo useradd -g users -G adm,root -s /bin/shell -p 123456 -d /home/testuser -m testuser
```I think this will create a new user called testuser with the password 123456

---

### Post by benerivo on 2007-12-20
rob1984, i've just tried the command i posted above to see if it works, and it didn't. I had to set the password separately. So you can use the command from my earlier post, but afterwards do this one```
sudo passwd testuser
```Then try to log in.

---

### Post by rob1984 on 2007-12-22
cheers but it seems to have fixed itself.

---

