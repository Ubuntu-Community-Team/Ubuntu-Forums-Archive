---
title: "Root password inconsistency"
date: 2006-04-17
forum: Desktop Environments
---

### Post by MvW on 2006-04-17
I supplied a root password during install, and this works fine in the terminal.  However, any access via gnome that requires some password fails, with error messages looking like this:

Failed to run gdmsetup as user root: Wrong password.

This happens for system admin functions, update manager, etc.

I logged in as a normal user at the startup screen.  Logging in as root at that point does not work. (I entered 'root' for user, then the pass)

---

### Post by Madpilot on 2006-04-17
Unless you did an expert install, the password you supplied during install is not root's, but your own user password. This is the only pw you need to run & administer a default Ubuntu system.

All of Ubuntu's graphical admin tools have been set up to use sudo & your own user pw, rather than a root pw.

[http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo) has more details.

---

### Post by MvW on 2006-04-17
[QUOTE=Madpilot]Unless you did an expert install, the password you supplied during install is not root's, but your own user password. This is the only pw you need to run & administer a default Ubuntu system.

All of Ubuntu's graphical admin tools have been set up to use sudo & your own user pw, rather than a root pw.

[http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo) has more details.[/QUOTE]

I did indeed do an expert install.  Now I have access to change the root password in terminal (I did that, BTW), but I don't have GUI sys admin access to even the clock.

---

### Post by xenmax on 2006-04-17
This thread and especially codejunkie's post should help solve your problem. I think it has to do with your user account not being a sudoer by default in expert install since root is enabled. [However, root login at GDM/start-up is not enabled :)]
This thread tells you how to add your user account to sudoer's list.
[http://www.ubuntuforums.org/showthread.php?t=146859]("http://www.ubuntuforums.org/showthread.php?t=146859")

Some might suggest to do a re-install in normal mode, but i also did an expert install and then followed instructions in above thread. Now i only use sudo and only use my normal password, with root account in terminal still enabled, but i have not faced any problems so far.

EDIT: edited for more clarity

---

### Post by MvW on 2006-04-17
[QUOTE=xenmax]This thread and especially codejunkie's post should help solve your problem. I think it has to do with your user account not being a sudoer by default in expert install since root is enabled. [However, root login at GDM/start-up is not enabled :)]
This thread tells you how to add your user account to sudoer's list.
[http://www.ubuntuforums.org/showthread.php?t=146859]("http://www.ubuntuforums.org/showthread.php?t=146859")
[/QUOTE]
Thanks.  I'm another happy reader of that thread, and your explanation makes sense, because I did try the root startup login as well.

---

