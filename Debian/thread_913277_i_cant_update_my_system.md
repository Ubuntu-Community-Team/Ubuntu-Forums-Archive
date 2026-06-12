---
title: "i cant update my system"
date: 2008-09-07
forum: Debian
---

### Post by hasanyaman on 2008-09-07
hi everyone 
i am writing to the command line "apt-get update" but it says 

"E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)E: Unable to lock the list directory"
than i tried this way "sudo apt-get update" but this time 
it says "administrator is not in the sudoers file.  This incident will be reported."
i suppose it causes from not being a root account 
i havent enough authorization or permission 
how can i open root account on my debian 4.0 etch
please help...

---

### Post by Sef on 2008-09-07
Moved to Debian Forum.

---

### Post by p_quarles on 2008-09-07
Debian does not come with sudo set up by default. To get root access, you'll need to use the "su" command:
```
su -c 'apt-get update'
```
and so forth. It will ask for the root password rather than for the user password. 

Setting up sudo to work the way it does in Ubuntu is easy, if that is what you are after.

---

### Post by markharding557 on 2008-09-12
Gnome and kde have a root console icon in the menu you can click on,it will ask you for your root password and away you go

---

