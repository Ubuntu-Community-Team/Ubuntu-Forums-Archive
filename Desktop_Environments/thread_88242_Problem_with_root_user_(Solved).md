---
title: "Problem with root user (Solved)"
date: 2005-11-09
forum: Desktop Environments
---

### Post by akonkwa on 2005-11-09
I have just installed ubuntu linux and I think I made a mistake. During installation, I typed the same password for the root and normal user account. Anyways, now I can't seem to switch to root. 

I tried going to systems --> Administration ---> User and groups
but i get prompted for my password and when I enter it , I receive an error message that says :

Failed to run users-admin:
Child terminated with 1 status

When I try other sudo commands from the ubuntu faq, the terminal answers that I am not in the sudoers list. But I can't edit that file unsless I'm root or able to do sudo...

Can anyone help me?

thanks

---

### Post by ssam on 2005-11-09
you should not have been asked for a root password during install (unless you did an expert install (i think)) sounds like you know about the whole sudo thing [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

sounds a bit bizzarre.

can you post the output of
```
id
```

this will show if you are in the admin group (the first use on the system should be, and if you are then you should be able to use sudo).

you might need to reinstall, or boot from a live cd and fix the sudoers file

---

### Post by DJ_Max on 2005-11-09
Unless something has changed with the Breezy install, Ubuntu doesn't ask for a root password.

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

Edit: looks like me and ssam posted at the same time :)

---

### Post by racecat on 2005-11-12
[QUOTE=DJ_Max]Unless something has changed with the Breezy install, Ubuntu doesn't ask for a root password.

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

Edit: looks like me and ssam posted at the same time :)[/QUOTE]

Nothing's changed. I've loaded Hoary and Breezy several times on one machine just messing around. You only put in a user password (twice to verify). When there is a command that requires root permission, you type in sudo (super user do) before the command, then THE password at the prompt. If you are starting a graphical program, you use gksudo instead; at least that is how I understand it.

It all sounds a little strange. Did you put in more than one user?

Bill

---

### Post by akonkwa on 2005-11-13
Thanks to you all for answering

I have got some help on an ubuntu irc channel and Musterd5 kindly helped me through my problem. I had done an expert install (because I naievely thought that it was the only way to obtain a dual boot) and had created a root user account that was password protected. I have got rid of it now, and I'm even conseidering getting rid of the dual boot itself (Windoz can be such a drag...), but I like gaming too much.... :-)

Thanks again to  everyone

---

### Post by tOpEzz on 2005-11-22
well done akonkwa... hehehhe...

---

### Post by upnorth on 2005-11-23
Hi,

I have the same problem, as I've noticed some others do when browsing the forums.  Any chance of placing the fix on here please.

Thanks

---

### Post by upnorth on 2005-11-24
Its Okay, have found the solution tucked away in another thread!!!

---

