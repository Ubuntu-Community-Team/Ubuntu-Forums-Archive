---
title: "Problem making shell script bootable"
date: 2006-08-13
forum: Desktop Environments
---

### Post by ATIR350 on 2006-08-13
Hi all

This post doesn't fit into the absolute newbie category
but maybe it's rather stupid

I was trying to make an Ubuntu internet router
using the Ubuntu internet router HOWTO
[http://www.ubuntuforums.org/showthread.php?t=111972](http://www.ubuntuforums.org/showthread.php?t=111972)

It worked pretty well except that I can't get the masquerading
shell script to run at startup

This is what I tried:
- went to terminal, typed sudo -i to get a root terminal
- copied my script into /etc/init.d directory by doing a
  cp /home/wilson/masqueradescript.sh /etc/init.d/masqueradescript.sh
- created a symbolic link in /etc/rc2.d by doing a
  ln -s /etc/init.d/masqueradescript.sh /etc/rc2.d/S95masqueradescript
- used the vim editor to check if the files were really there
- restarted the computer, but the script failed to run
  ( I checked that by trying to trying to access the internet on a connecting computer)
- run the shell script manually, the connecting computer accesses the internet properly


Is there anything I did wrong or have the autostart directories changed or sth? 
thx!

---

### Post by ATIR350 on 2006-08-13
My system is running Ubuntu Dapper Drake desktop
with GNOME

---

### Post by ardchoille on 2006-08-13
> **ATIR350 said:**
> Hi all

This post doesn't fit into the absolute newbie category
but maybe it's rather stupid

I was trying to make an Ubuntu internet router
using the Ubuntu internet router HOWTO
[http://www.ubuntuforums.org/showthread.php?t=111972](http://www.ubuntuforums.org/showthread.php?t=111972)

It worked pretty well except that I can't get the masquerading
shell script to run at startup

This is what I tried:
- went to terminal, typed sudo -i to get a root terminal
- copied my script into /etc/init.d directory by doing a
  cp /home/wilson/masqueradescript.sh /etc/init.d/masqueradescript.sh
- created a symbolic link in /etc/rc2.d by doing a
  ln -s /etc/init.d/masqueradescript.sh /etc/rc2.d/S95masqueradescript
- used the vim editor to check if the files were really there
- restarted the computer, but the script failed to run
  ( I checked that by trying to trying to access the internet on a connecting computer)
- run the shell script manually, the connecting computer accesses the internet properly


Is there anything I did wrong or have the autostart directories changed or sth? 
thx!

Did you make the script executable with chmod u+x script.sh ?

---

### Post by ATIR350 on 2006-08-14
That worked like a charm
Thx!!!:KS :KS

---

### Post by ardchoille on 2006-08-14
> **ATIR350 said:**
> That worked like a charm
Thx!!!:KS :KS

Glad to hear it's working :)
You're welcome.

---

