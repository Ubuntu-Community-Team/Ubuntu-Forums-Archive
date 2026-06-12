---
title: "Help 4 a newb in networking Ubuntu"
date: 2005-05-31
forum: Desktop Environments
---

### Post by mahirudeyume on 2005-05-31
As stated prior I'm a newb to linux.  I have read a few posts that say to get Ubuntu to see the windows network i need to install samba and smbfs.  Both are installed but when i go to networking the general tab doesnt have the windows network tab that the posts refer to.  What am i missing?  I dual boot XP pro and it connects to the other systems no problem.  Thanks in advance for any help and the Ubuntu forum community is a great source for info!

---

### Post by [pl]ice on 2005-05-31
konqueror got a function to look through network, that what i used; 
maybe helps,

you can also check for the other box
eg:
michal@pirat:~$ net share -I ip
ip of the other box, and then should prompt for password; if this doesn't work then might be a problem....
there is a howto on mounting vi fstab at bootup, might help.
p.s. don't worry i'm new as well 
 :grin:

---

### Post by elatomo on 2005-05-31
Do you use firestarter? If you use it try to stop the firewall and then refresh the windows network window.

Also check if the domain name in the system>network>general tab matches the name of your windows workgroup (i'm not too sure about the names of the menues because i use a non-english desktop)

---

