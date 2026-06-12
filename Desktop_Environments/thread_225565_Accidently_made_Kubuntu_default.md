---
title: "Accidently made Kubuntu default"
date: 2006-07-29
forum: Desktop Environments
---

### Post by slimgarfield on 2006-07-29
I installed KDE using the command

sudo apt-get install kubuntu-desktop

Then i got a message asking if i wanted to make KDE or Gnome default.  I accidently chose KDE.  Now i can no longer change the login window and when i log into gnome, i cant shutdown.  I have to logout and then shutdown.  Is there any way to change the default back to gnome so i can change my login window again? I have tried to reinstall ubuntu-desktop through synaptic, but it didnt change anything.  I have ubuntu 6.06 installed if it changes anything.

---

### Post by harryhoudini66 on 2006-07-29
Have you tried logging out. Then on the login menu select Options/Select Sessions/GNOME?

You then will not be asked if you want to make it your default session.

---

### Post by slimgarfield on 2006-07-29
Sorry if i didnt make it clear, but i can log into gnome, and i can make it the default session, but i cannot shutdown from gnome nor change the login window.  I really dont like the login window that KDE uses and would like to use another one.

---

### Post by aysiu on 2006-07-29
Try ```
sudo nano -B /etc/X11/default-display-manager
``` Change it from /usr/bin/kdm to /usr/sbin/gdm. Then Control-X, Y, Enter to save.

---

### Post by slimgarfield on 2006-07-30
aysiu, although i would have thought that would have worked, but now i have to login through the command prompt.  I then run startx and i can get back in.  Any ideas on why this is happening?  Thanks for that advice though.

---

### Post by slimgarfield on 2006-07-30
I just looked in my urs/bin/ folder and i couldnt find gdm.  I think thats the problem, how should i get that back?

---

### Post by aysiu on 2006-07-30
> **slimgarfield said:**
> I just looked in my urs/bin/ folder and i couldnt find gdm.  I think thats the problem, how should i get that back?
It's /usr/sbin/gdm, not /usr/bin/gdm

---

### Post by iamhugeinjapan on 2006-07-30
It stands to reason that (re)installing gdm would give you the choice of choosing login managers again too yes?

---

### Post by slimgarfield on 2006-07-30
Ah, i didnt catch that it was in sbin.  That fixed the problem.  Thanks alot.

---

