---
title: "Block Website Access"
date: 2009-05-21
forum: General Help
---

### Post by Psycho.mario on 2009-05-21
This may not be in the right place but here goes:

I have two computers on my LAN, both connected by ethernet, my computer is running Ubuntu 9.04, the other is running Windows XP. I want to block access to certain websites on the _**XP**_ computer. I'd rather not install anything on the XP machine. Is it possible?

In short: Can i block websites from an Ubuntu machine on an XP machine over ethernet?

Thanks in advance

Psycho.Mario

---

### Post by mcduck on 2009-05-21
No, Ubuntu machine has absolutely no control over the XP machines network usage unless the XP machine is connected to network *through* the Ubuntu machine.

You could block websites in Windows using the hosts file (which doesn't require installing any extra programs) or, if you use a router/switch it might have the capability to restrict connections based on IP address.

---

### Post by Bucky Ball on 2009-05-21
Buy a router with good configuration options or setup some software on the Windows box.

---

### Post by Psycho.mario on 2009-05-21
I know this is blatantly the wrong place, but where is the hosts file in windows and how does it work? I think that could be an option i could use

---

### Post by ephmanjmm on 2009-05-21
c:\windows\system32\drivers\etc

---

### Post by Psycho.mario on 2009-05-21
Thanks, I got the hosts file to work

---

