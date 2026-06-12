---
title: "Select Root Authority in Dolphin"
date: 2011-09-30
forum: Desktop Environments
---

### Post by mhumm2 on 2011-09-30
Hello;

I have a couple of folders set up as root only access and I would like the ability to access those folders from  Dolphin run as a user with password protection.

Specifically, I'd like the functionality that when I access those protected folders a password prompt window appears and allows the user (me) to enter the root pw and open.

I have been doing this via terminal, but I would like an elegant kde solution if possible.  

Now that I'm thinking about it.  Can different folders have different passwords??? 

Thanks.

---

### Post by oobuntoo on 2011-10-01
> **mhumm2@bellsouth.net said:**
> Hello;

I have a couple of folders set up as root only access and I would like the ability to access those folders from  Dolphin run as a user with password protection.

Specifically, I'd like the functionality that when I access those protected folders a password prompt window appears and allows the user (me) to enter the root pw and open.

I have been doing this via terminal, but I would like an elegant kde solution if possible.  

Now that I'm thinking about it.  Can different folders have different passwords??? 

Thanks.

Are you letting someone use your account but don't want that person to see your pr0n collection? There are lots of way to password-protect files/folders under Linux, but I don't think there's "an elegant kde solution" the way you want. 
- If you don't want another user on the same computer/OS to see folder/file, you can change read/write/execute permission of that file. People with root access can still see it.
- If you don't want anyone at all (whether they have root access/using your account or not) to see it, then I suggest TrueCrypt.
- You can also check out Kgpg (it's more like archive plus encryption) to see if that would work for you.

---

### Post by perspectoff on 2012-05-05
kdesudo dolphin

will start the Dolphin file manager as the root user (requiring the root password). You can make this command into a menu item.

If you haven't set the root password, do so:

 sudo passwd root

When you open a file from Dolphin once it is opened as the root user (such as with the text editor kate) you will be doing so with root privileges. Very handy.

You can also start dolphin as the root user from the command line using

 sudo dolphin

but you can't use this command as a menu item.

---

