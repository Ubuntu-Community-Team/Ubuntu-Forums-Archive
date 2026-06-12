---
title: "Remote desktop to Ubuntu"
date: 2005-11-17
forum: Desktop Environments
---

### Post by Terrik on 2005-11-17
Hi all,

I know there is probably a guide somewhere in these forums for connecting to an ubuntu 5.10 machine from Windows XP via remote desktop, but I can't find one. 

Can anyone link a guide here or help with detailing the steps. Thanks!

---

### Post by Roman27 on 2005-11-17
It's very easy to do.  Here you go, step-by-step:

1. Obtain the RealVNC client from [http://www.realvnc.com](http://www.realvnc.com) and install it on your Windows XP machine.
2. Turn on the Remote Desktop feature in Ubuntu by going to *System* -> *Preferences* -> and *Remote Desktop*.  Then click on the checkbox to **Allow other users to view your desktop**.  The other options are up to you.  I would suggest you set a password.  That's it!

---

### Post by Terrik on 2005-11-17
Awesome, thanks!

---

### Post by Roman27 on 2005-11-17
You're most welcome.  :)

If you want something a bit faster and more secure, you can do a search on this board for "FreeNX" (look here too [https://wiki.ubuntu.com/FreeNX](https://wiki.ubuntu.com/FreeNX)).  It's a bit more challenging to setup, but you won't be left unrewarded in the end.

---

### Post by Terrik on 2005-11-18
Hey again,

When I add the repository stated in the wiki to my apt-sources and do an update, it can't connect to the server and when I go to 

[http://seveas.ubuntulinux.nl](http://seveas.ubuntulinux.nl)

It says the connection failed. Does anyone know if the address for this repository changed, or another repository where I can get a recent version of FreeNX? Thanks.

---

### Post by thegnark on 2005-11-18
[quote=Roman27]It's very easy to do.  Here you go, step-by-step:

1. Obtain the RealVNC client from [http://www.realvnc.com]("http://www.realvnc.com") and install it on your Windows XP machine.
2. Turn on the Remote Desktop feature in Ubuntu by going to *System* -> *Preferences* -> and *Remote Desktop*.  Then click on the checkbox to **Allow other users to view your desktop**.  The other options are up to you.  I would suggest you set a password.  That's it![/quote] 
Is there somewhere where I can set this by command line? I have SSH running and would like to enable VNC.

---

### Post by bookemdano on 2005-11-18
[QUOTE=Terrik]Hey again,

When I add the repository stated in the wiki to my apt-sources and do an update, it can't connect to the server and when I go to 

[http://seveas.ubuntulinux.nl](http://seveas.ubuntulinux.nl)

It says the connection failed. Does anyone know if the address for this repository changed, or another repository where I can get a recent version of FreeNX? Thanks.[/QUOTE]

If anyone knows of an alternative download site for freenx, please post it here.  TIA.

---

### Post by pete on 2005-11-18
I had the same problem with the seveas repository that is listed in the wiki, but was eventually able to get it *i think* out of the hoary-backports (didn't see if you were running Hoary or Breezy, so not sure if this will work for you).

In general, though, I'd definitely recommend FreeNX over VNC.  Your machine doesn't have to be logged in for you to connect to it (this is *possible* with VNC, but involves a lot of rigamarole), and the quality of the connection is MUCH better with FreeNX since the compression takes places at the X level.

---

### Post by Roman27 on 2005-11-21
Make sure you follow the directions here: [https://wiki.ubuntu.com/FreeNX](https://wiki.ubuntu.com/FreeNX).  That includes going to the [http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/) site and adding the gpg keys using the two command lines given on that page.  It looks like
```
gpg --keyserver subkeys.pgp.net --recv-keys 1135D466
gpg --export --armor 1135D466 | sudo apt-key add -
```
and then do a
```
sudo apt-get update
```
You should no longer get errors about the seveas repository.

---

