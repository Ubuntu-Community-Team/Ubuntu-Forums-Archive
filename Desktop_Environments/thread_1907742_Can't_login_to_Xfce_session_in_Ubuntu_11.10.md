---
title: "Can't login to Xfce session in Ubuntu 11.10"
date: 2012-01-12
forum: Desktop Environments
---

### Post by ADeadCat on 2012-01-12
So, I had installed xfce before, when I was messing around with desktop environments, but I got busy again, and decided to uninstall it. Purged/removed as many xfce-related files as possible, and deleted /usr/share/xsessions/xfce.desktop with rm. Recently reinstalled xfce, but now I can't login to xfce session. Help/suggestions?

---

### Post by tomski on 2012-01-12
try to re-install it (in place) then 
cat /usr/share/xsessions/xfce*
cat /usr/share/xsessions/xubuntu*
see if you get results

if not open root terminal and re-create with following contents:

```

[Desktop Entry]
Version=1.0
Name=Xfce Session
Comment=Use this session to run Xfce as your desktop environment
Exec=startxfce4
Icon=
Type=Application

```

if that fails 'completely remove' xfce AND it's components & re-install then re-try 

or you could try to install:
xubuntu-desktop

---

### Post by ADeadCat on 2012-01-12
Re-creating xfce.desktop worked, thanks a lot for the help.

---

### Post by tomski on 2012-01-12
no prob's :)

don't forget to mark as solved ;)

---

### Post by sub_acoustic on 2012-03-12
this was such a hassle, especially as all the rm .Xauthority suggestions made by others didn't work...  

I found the solution eventually thanks to another ast I can't refind to thanks

but the solution was to move then recreate my user profile
> 
sudo mv /home/USERNAME /home/backup
sudo mkdir /home/USERNAME
sudo chown USERNAME:USERNAME /home/USERNAME

easy...then login

---

### Post by whitefort on 2012-05-13
Thanks for this post, sub_acoustic - you've just got me out of a LOT of trouble!!!

(I upgraded someone else's computer, then found that they couldn't get into their desktop.  Now I'm a hero again!!  :)

---

