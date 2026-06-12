---
title: "A user can't login to its desktop after password change"
date: 2010-12-22
forum: Desktop Environments
---

### Post by TheLugal on 2010-12-22
Hey all!

One of my users has a bit of a problem. I forced password change for this user, and the user thought that it was simply asking for the password again. I had to use my godlike powers to change the users password again. And here comes trouble.

The user cannot log in. The system accept the password and we can see the background screen and some messages, but that is all.

> Could not update ICEauthoroty file /home/user/.ICEauthoroty
> There are problems with configurationsserver.
(/usr/lib/libgconf2-4/gconf-sanity-check-2 exit with status 256)
> Nautilus couldn't create following folders necessary: /home/user/Desktop, /home/user/.nautilus.

Please create these folders before you run Nautilus, or set permission so Nautilus can create them.
(Note; these messages are translated by me.)

I think it can have something to do with encrypted home folders, but I am not sure.
Do anyone know how I can fix this?

---

### Post by Nimbus200 on 2010-12-22
Maybe :
- Login as root ( Alt + Ctrl + F1 to get tty1)
- # chown youruser:youruser /home/youruser/.ICEauthority

make your youruse has full rights to the home directory
 # chown -R youruser:youruser /home/youruser

---

### Post by TheLugal on 2010-12-22
Sorry, I'm not sure if I quite got that. However, you gave me the idea to SSH into this users terminal. (I learned about "Alt + Ctrl + F1" recently, and haven't got how to get out of it yet.)

As this problem is for just a regular user, and not my own sudoer, I can log in with my own user, and use that terminal.

I found that the problems probably is because the homefolder is encrypted, and the password don't work. (Not even the old one).
This is bad :icon_frown:

---

### Post by Nimbus200 on 2010-12-22
"...The system accept the password and we can see the background screen and some messages, but that is all..."

That means the user CAN login and new password is accepted.
But the user is having problem somewhere else in the system.
Alt + Ctrl + F1 is tty1. You can use other F keys ( F2, F3...) to get to the other tty. The GUI is usually on F7 or F8.

If you can login with superuser privillege to system ( directly or via ssh ) check the user's right on the /home/user/.ICEauthoroty
The user must have read and write access to it.
Moreover, check the user's right on its own home folder.
You can do that by login via ssh or using other tty other than tty used by GUI

---

### Post by TheLugal on 2010-12-23
Well, I can't it's encrypted... And correct me if I'm wrong, but there isn't much to do, is it?:(

UPDATE;
After wild guessing I managed to find the correct password. It would seem like the user has to change its own password. If not, the system will only change password for the user, and not the encrypted home-folder. Lesson to be learned; do NOT lose your password when using encrypted home folders!

Thank you very much for your help Nimbus200! I learned a few things in the process! :D

---

