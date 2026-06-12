---
title: "gdm seems to ignore /etc/gdm/Init/Default"
date: 2008-05-30
forum: Desktop Environments
---

### Post by akira666 on 2008-05-30
I'm having an issue where gdm seems to not execute /etc/gdm/Init/Default. The file has execute permissions, but doesnt seem to do anything. Specifically I am trying to start synergy for the login screen, but no go. I have it working after login no problem.

I tried putting a 'touch /tmp/bleh' in the Default, and that never seems to get executed.

I'm running the latest 8.04.

Thanks for any help,
-Tom

---

### Post by akira666 on 2008-06-01
No one has any ideas eh?

---

### Post by sdennie on 2008-06-01
Have you tried putting things in /etc/gdm/Xsession?  Putting a simple "touch /tmp/itworked" there works fine after a Ctrl-Alt-Backspace.

---

### Post by akira666 on 2008-06-01
It seems to pickup stuff in Xsession, unfortunately I need it for the login screen :|

---

### Post by sdennie on 2008-06-01
I'm not sure what synergy is or exactly what you are trying to do but, you could make an init script that starts your command before gdm (assuming synergy doesn't depend on $DISPLAY) or, even more brute force, edit /etc/init.d/gdm and start your command before gdm is started.  There may be a more elegant solution but, I'm not aware of it.

---

### Post by akira666 on 2008-06-01
Synergy is a program that lets you share mouse+kb from one "server" pc with other "clients" over a network. I have it working once logged in, but to be really effective it would of course need to work for the login screen as well! It does need the x server to attach to, so the first option may not work, but I will look into changing /etc/init.d/gdm, that might be an option.

Thanks for the ideas!

---

### Post by akira666 on 2008-06-03
I fixed it... I switched to kdm ;)

---

### Post by alibaba163 on 2010-06-14
hello, 
      I want to do similar thing. I have a remote control (desktop control) application where the Client has to be available at login screen so that the server can connect to it.

Can you please tell me what you do after switching to kdm desktop(kde desktop environment) ??? do u imply switching to kde desktop environment or you imply switching to kdm as a display manager for gnome environment???

Your help would be appreciated


Regards,

alibaba

---

