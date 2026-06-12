---
title: "Problem with sudo and relatives"
date: 2007-10-31
forum: Desktop Environments
---

### Post by ngoncalves on 2007-10-31
I after installing Ubuntu 7.10, I changed root password (which by default was the same as the initial user I created) and also removed administrative privileges to user created during the installation procedure.

The problem is that, after doing this, sudo and gksudo stoped working. When I try to run some administrative stuff, I get the window asking for the administrator (root) password. But when I type it, all I get is an error. And if I type the wrong password I get a different error !

The strangest thing is that I can open a console, type "su" and login as root. Any has suggestions on how to fix this ?

Thanks

---

### Post by schorem on 2007-10-31
With sudo it does not ask for the root password but for the password of the user. Did you try that password?

---

### Post by ngoncalves on 2007-10-31
Yes, I have tried with the user password. I still get an error message saying that the user does not have admin privileges (wich is correc).

What I did was: 
 
   1) pressed ALT + F2 to get the "command-line" window

   2) wrote "gksudo synaptic" 

   3) Entered the user password when requested by a new window
  
 The weirdeste thing is that after doing this once, I could not repeate it again. That is, after setp 2, nothing more happens, No window asking for a password and no program executing. I tried to reboot and it happened again. The first time I get an error, and thereafter nothing happens after step 2.

What am I doing wrong here ?

---

### Post by ngoncalves on 2007-10-31
I have found this document about [sudo and the root account in Ubuntu]("https://help.ubuntu.com/community/RootSudo#head-c625ac47fd3adc6178d573a652c589bf4ebedab5") and figured out where I messed up.

Although I use linux for a long time, it was my first try at Ubuntu. And I was under the impression that a root account was required. That is why I removed all administrator privileges to my normal user account and created the root account. And that is why I cannot  sudo, although probably not why the window requesting the password does not appear.

So now I need to give back administrator privileges to my normal user account and remove the root account. Any hints on how to do this, without using sudo ?

---

### Post by ngoncalves on 2007-10-31
I finally solved the problem:

 1) Opened a terminal, and became root with "su -"

 2) As root, added my normal user account to the administrators group with 
     "usermod -a -G admin username"

 3) exit the root login, and as normal user locked the root account:
    "sudo passwd -l root"

 Hope this helps anybody else having similar problems.

---

