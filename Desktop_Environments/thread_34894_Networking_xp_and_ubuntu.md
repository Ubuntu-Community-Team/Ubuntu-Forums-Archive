---
title: "Networking xp and ubuntu"
date: 2005-05-16
forum: Desktop Environments
---

### Post by Dave88 on 2005-05-16
I'ev been trying to network my laptop which runs windows xp with ubuntu destop but so far the xp machine can't access the ubuntu machine, i get some sort of error and the ubuntu machine can't even see the xp machine!

I have both machines set on Mshome and the ubuntu machine has two smb shares.

Anyone know what I'm doing wrong??
thanks!

---

### Post by defkewl on 2005-05-17
Can you ping to each machine?

---

### Post by Dave88 on 2005-05-17
yeah I can ping between the two machines, 0% packet loss and they both take roughly the same time

---

### Post by shakin on 2005-05-17
[QUOTE=Dave88]yeah I can ping between the two machines, 0% packet loss and they both take roughly the same time[/QUOTE]

How are you mounting the shares? Try with the IP address instead of the name: //192.168.1.100/share

---

### Post by Dave88 on 2005-05-17
All of a sudden everything works!!
except the linux shares are asking for a password i didn't set!

I tried sudo sambapasswd but it wont let me set the passwords!

---

### Post by stepore on 2005-05-17
[QUOTE=Dave88]All of a sudden everything works!!
except the linux shares are asking for a password i didn't set!

I tried sudo sambapasswd but it wont let me set the passwords![/QUOTE]
 so far, you've provided absolutely no information.
what you've done?
how are you trying to connect?
what are the error messages, *exactly*.

since we have no info:
man smbpasswd
look for the '-a' option.

---

