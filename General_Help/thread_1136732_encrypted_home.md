---
title: "encrypted home"
date: 2009-04-25
forum: General Help
---

### Post by linux_ocean on 2009-04-25
Hi I want to see whether my home partition is encrypted or not.
but i don't know how can i check it.
if my home partition isn't encrypted, how can i encrypt it?
i am using ubutu 9.04.

---

### Post by linux_ocean on 2009-04-26
Is home partition encryped by defult, when i install a fresh copy of ubuntu 9.04?

---

### Post by bluefrog on 2009-04-26
no

the simplest if you want to encrypt your home is to create a new user with encrypted home and then transfer your files to the new user.

sudo adduser --encrypt-home

---

### Post by linux_ocean on 2009-04-26
Thank you dear 'bluefrog'. I have added a new user with encrypted home.

> hossein@polaris-desktop:~$ sudo adduser monir --encrypt-home
Adding user `monir' ...
Adding new group `monir' (1001) ...
Adding new user `monir' (1001) with group `monir' ...
Creating home directory `/home/monir' ...
Setting up encryption ...

************************************************************************
YOU SHOULD RECORD THIS MOUNT PASSPHRASE AND STORE IN A SAFE LOCATION:
39e842095a245717e8a745d53427fcf7
THIS WILL BE REQUIRED IF YOU NEED TO RECOVER YOUR DATA AT A LATER TIME.
************************************************************************

Warning: Using default salt value (undefined in ~/.ecryptfsrc)

Done configuring.

Copying files from `/etc/skel' ...
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
Changing the user information for monir
Enter the new value, or press ENTER for the default
	Full Name []: Monireh
	Room Number []: 
	Work Phone []: 
	Home Phone []: 
	Other []: 
Is the information correct? [Y/n] y
hossein@polaris-desktop:~$ 


when i loged in with new user i was created, i saw the window bellow:

[[IMG]http://www.gigaimage.com/images/2hkbivn2jamlx82vdt_thumb.png[/IMG]](http://www.gigaimage.com/viewer.php?file=2hkbivn2jamlx82vdt.png)

so i clicked on "Run this action now" button and then set a new passphrase.

but the questions are:
             
           1. How can i recover my private data? (for example with root)
           2. Can anyone to delete my home with root access?

---

### Post by karlh626 on 2009-07-30
the root user can delete the home directory.

---

### Post by zzzBrett on 2009-07-30
> **linux_ocean said:**
> 
             
           1. How can i recover my private data? (for example with root)


What do you mean recover your private data?  Do you mean will you be able to access it without a password once it is encrypted?

---

