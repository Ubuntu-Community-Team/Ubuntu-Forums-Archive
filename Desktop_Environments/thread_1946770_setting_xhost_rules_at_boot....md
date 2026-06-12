---
title: "setting xhost rules at boot..."
date: 2012-03-25
forum: Desktop Environments
---

### Post by yurtesen on 2012-03-25
I am able to set xhost at boot in Fedora by editing /etc/gdm/Init/Default and for example add:

/usr/bin/xhost +local:

How can similar be done in Ubuntu? I want that the

/usr/bin/xhost +local:

command is executed when the system is sitting at login prompt.

---

### Post by Paddy Landau on 2012-03-26
Do you want it executed when the computer turns on (before showing the login screen) or after you have logged in?

To execute a command after you have logged in, add the command to [FONT=Lucida Console].profile[/FONT] in your home folder (this will apply *only* to you).

To execute a command when you or anyone else logs in, add the command to [FONT=Lucida Console]/etc/profile[/FONT].

To execute a command before anyone logs in, add the command to either [FONT=Lucida Console]/etc/rc.local[/FONT] or [FONT=Lucida Console]/etc/gdm/Init/Default[/FONT] (I don't know the difference between the two, so I don't know which one is preferable).

---

### Post by yurtesen on 2012-03-26
> **Paddy Landau said:**
> 
To execute a command before anyone logs in, add the command to either [FONT=Lucida Console]/etc/rc.local[/FONT] or [FONT=Lucida Console]/etc/gdm/Init/Default[/FONT] (I don't know the difference between the two, so I don't know which one is preferable).

Thank you for the answer, This is the correct answer if ubuntu was using GDM (the Init/Default one). If I put it to /etc/rc.local, I believe it wont work since only the user who starts GDM would have right to change xhost setting.

However, since Ubuntu is using Lightdm at this point. I was looking for something which would work with lightdm. For now, I could solve the issue by giving shell to lightdm, setting DISPLAY=:0 in shell rc file and running su - lightdm -c xhost +local: from the rc.local. This is not quote elegant...

---

