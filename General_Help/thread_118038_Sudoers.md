---
title: "Sudoers"
date: 2006-01-16
forum: General Help
---

### Post by Twizz on 2006-01-16
Hello, Every time I try to open up Root Terminal or anything that needs a password to get access it wont start up.  When I type in the Terminal anything with Sudo I get this error:
>>> sudoers file: syntax error, line 23 <<<
sudo: parse error in /etc/sudoers near line 23

Anybody have any ideas?  I think I messed it up when setting Firestarter to start up withough the need for a password.  I think I placed  "username ALL=NOPASSWD:/usr/sbin/firestarter" wrong (I did change "username" to mine)

---

### Post by jrib on 2006-01-16
Replace your /etc/sudoers with a default one (I attached mine below).  Did you use ```
visudo
``` to edit your sudoers file (you should have)?  Actually, you really shouldn't even be editing it anyway.  1)You probably don't need a firewall, 2) firestarter's gui doesn't need to be running for your firewall to work.  If you really need the gui to start up everytime, wait a few days/weeks until you get more comfortable.

If you can't get superuser privileges to edit /etc/sudoers, either boot in recovery mode or boot with a livecd and mount '/'.  Then just replace your sudoers on your linux partition with the one I've attached.

---

### Post by newuser111 on 2006-01-16
you don't add firestarter to the sudoers file, that file should not be edited unless you want to add sudo privileges to new users, i am curious on how you came to believe you needed to add /usr/sbin/firestarter to the sudoers file...

---

### Post by Twizz on 2006-01-16
I read this thread:  [http://www.ubuntuforums.org/showthread.php?t=26483](http://www.ubuntuforums.org/showthread.php?t=26483)

---

### Post by Twizz on 2006-01-16
I replaced sudoers with the one you attached.  Thanks for your help.  Even though this kinda of sucked... I kinda like messing up and learning new stuff... :razz:

---

