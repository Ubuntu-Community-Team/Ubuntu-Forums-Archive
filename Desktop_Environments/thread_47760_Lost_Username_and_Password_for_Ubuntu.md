---
title: "Lost Username and Password for Ubuntu"
date: 2005-07-09
forum: Desktop Environments
---

### Post by Fenix on 2005-07-09
I haven't used my Ubuntu Linux PC in a while but, now when I have tried to use it the user name and password I used, the user name and password I use for everything, doesn't work. Now I have two questions.

1. Is there anyway to find out what it is?

2. If not, Is there a way to make a new user name?

I have stuff on their.(I use it for storage mostly) So, reinstalling isn't an option and I don't think I put my home folder on a separate partion but, I'm going to redownload Ubuntu and find out.

Thanks in advance.

---

### Post by aggiechemist on 2005-07-09
First off, I assume that the user you are having a problem with is not "root." You know, the all power system administrator profile. I assume this because Ubuntu pretty much forces you to use a different user for almost all of your work. If you have forgotten your root password, you have a larger problem (I'll work on this at the end). However, if you can log in to root we can probably fix this up. 

The default configuration does not allow you to log into root through the nice pretty visual interface at bootup, but must be accesed through the command line.

To get to the command line, you will need to press Ctrl+Alt+F1 (or F2, or F3, etc.)

This should get you to a prompt asking you to log in. Log in as root and use the root password. 

Now you have a great deal of power. The easiest thing to do would be to enter the command passwd username, where you put in the username of the broken account in the obvious place. You can then just type in a new password.

And no, you cannot lookup the old password. Linux has far too much encryption for that.

If you have forgotten the root password, taht can be dealt with as well but is tougher. If taht is the case, post again and I will go and look up the workaround for it.


Good luck.

---

### Post by adwait on 2005-07-09
Hi,

Well, if u know the root password, do this:

While system is booting up, at the grub screen press 'e' to edit the boot command and then add a '1' at the end of the whole command and continue booting. That should get you in single user mode. There login as root....
Now change the password of the user you want with passwd <user>.

Adwait

---

### Post by Fenix on 2005-07-10
Thanks you guys. Doing this has shown me that my friend had deleted the my account. I only know because the root account and password are the combination he always uses and when I try to change my account password it says it's nonexistent.

I was able to recreate my account and save my files though. Thanks for the help all.

---

