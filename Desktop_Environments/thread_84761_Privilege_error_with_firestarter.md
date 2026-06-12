---
title: "Privilege error with firestarter"
date: 2005-10-31
forum: Desktop Environments
---

### Post by Terrik on 2005-10-31
Hi all,

I am using XFCE4 and firestarter. I edited my sudoers file and inserted:

username ALL= NOPASSWD: /usr/sbin/firestarter

and replaced 'username' with my username, then I created a startup script to load firestarter on bootup, which contains this line:

sudo firestarter --start-hidden

But when my session starts, I get this error:

"Insufficient privileges: You must have root user privileges to use Firestarter"

and the strange part about all this...Firestarter loads perfectly and is up there running on the taskbar like it should be doing as I get this error.

Does anyone know how I can get rid of this error?? Thanks.

---

### Post by Terrik on 2005-11-01
Anyone know?? Please?

---

### Post by flyingbrass on 2005-11-01
Put your firestarter entry last in sudoers, below the %admin line.

Thanks go to whoever first posted this solution for saving what remains of my hair.

---

### Post by Terrik on 2005-11-20
I do already have the line at the bottom of my sudoers. It just makes no sense. 

Anyone else experience this problem with XFCE4?

---

### Post by SickTwist on 2005-11-20
[QUOTE=Terrik]Hi all,

I am using XFCE4 and firestarter. I edited my sudoers file and inserted:

username ALL= NOPASSWD: /usr/sbin/firestarter

and replaced 'username' with my username, then I created a startup script to load firestarter on bootup, which contains this line:

sudo firestarter --start-hidden

But when my session starts, I get this error:

"Insufficient privileges: You must have root user privileges to use Firestarter"

and the strange part about all this...Firestarter loads perfectly and is up there running on the taskbar like it should be doing as I get this error.

Does anyone know how I can get rid of this error?? Thanks.[/QUOTE]

Firestarter is just a graphical interface to configure the Linux firewall. After Firestarter has been installed, the firewall is automatically enabled every time that the computer boots. The only time you need to run Firestarter is when you want to *configure* the firewall. There is no need for every user to be able to start Firestarter.

---

### Post by shadow07 on 2005-11-22
[QUOTE=SickTwist]Firestarter is just a graphical interface to configure the Linux firewall. After Firestarter has been installed, the firewall is automatically enabled every time that the computer boots. The only time you need to run Firestarter is when you want to *configure* the firewall. There is no need for every user to be able to start Firestarter.[/QUOTE]

Right.  But, I would want some kind of indication there has been a policy violation.  The only way is to have the GUI start hidden.

I get the same thing.  It appeared after the recent update to sudo from the repositories.

I too would like to resolve this issue.  Maybe the format has changed for the sudoers file?


@ TERRIK:
Did you use visudo to edit the sudoers file?  Or simply gedit?

---

### Post by stuart-newtoubuntu on 2006-01-14
I have had exactly the same problem with Xfce from when I started using it. The same problem has recently started with gnome even though firestarter has been working perfectly, for the past two months. 

My problems seemed to start after I did a sudo apt-get update.

But as I am a complete newbie I have no idea how to fix it.

---

### Post by Ocxic on 2006-01-15
I'm having the same problem, I'm running Gnome however, with metacity WindowManager if that means anything. happend after i did an update too.

---

