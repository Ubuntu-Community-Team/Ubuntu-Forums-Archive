---
title: "[SOLVED] Problems accessing my gnome desktop"
date: 2007-11-24
forum: Desktop Environments
---

### Post by Tabenx on 2007-11-24
I had recently changed my GDM theme and after i restarted i couldn't access the desktop. Right now i'm making this post from the command lind using lynx. Can someone help me? The error said it could not access the greeter or something.

---

### Post by scxtt on 2007-11-24
sounds like a problem w/ the theme ... what happens when you do the following:

sudo /etc/init.d/gdm stop
startx

you should be able to **startx** regardless of some problem w/ gdm ...

---

### Post by Tabenx on 2007-11-24
it says 
xauth: creating new authority file /root/.serverauth.5586
Fatal server error:
server is already active for display 0
   if this server is no longer running, remove /tem/.X0-lock and start again

it says a lot more but i decided since i can now access the internet via lynx i'll just email myself the files and reinstall ubuntu. Thanks for your help though!

---

### Post by scxtt on 2007-11-24
i'm sure it's solvable ("*if this server is no longer running, remove /tmp/.X0-lock and start again*"), but a reinstall will get the job done too :p ...

---

### Post by Tabenx on 2007-11-24
hmmm actually since i cant seem to attach my files in gmail with lynx, can you tell me how to fix it?

---

### Post by scxtt on 2007-11-24
what do you get if you run the following command?:

ls -l /tmp/.X0-lock

if that file exists, delete it ( rm /tmp/.X0-lock )

also, a reboot may clean things up ... i'm sure you can set  the GDM theme in gdm.conf as well.

---

### Post by Tabenx on 2007-11-24
it says file does not exist

---

### Post by scxtt on 2007-11-24
did you try a reboot?

what does **ls -l /tmp/*lock** return?

if all you did was change a GDM theme, i doubt it could totally hose up X ...

---

### Post by Tabenx on 2007-11-24
I managed to startx but i had no internet access and i couldnt access the login theme thing

---

