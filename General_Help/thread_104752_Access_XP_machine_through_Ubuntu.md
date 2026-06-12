---
title: "Access XP machine through Ubuntu"
date: 2005-12-16
forum: General Help
---

### Post by bingerthedog on 2005-12-16
I just setup a Ubuntu Samba/SSH machine and that is all working great.  I can use SSH from a remote location to access files on the Ubuntu machine and I can use Samba to store files from my XP machine onto the Ubuntu machine.  But now I was thinking it would be nice if I could use SSHVNC to access the Ubuntu machine and then on the Ubuntu machine I want to go to Places and then Network Servers to access my XP machine through Ubuntu.  Does anyone know how to do this?  I can see my XP machine through the Network Server but it won’t let me connect to it.  Any ideas?  It would be nice to access files that I haven't yet transferred to the Samba server.

---

### Post by Stereotypical Rage on 2005-12-16
Unfortunately my girlfriend loves Microshaft and I'm forced to support them. (evil things MS be.) 

I have a home LAN and Breezy/Hoary saw her Laptop/Desktop out of the box. I can transfer files between the two with no issue. No extra settings required.

Is this what you want? Or did you want a Remote Desktop/VNC session?

---

### Post by soulestream on 2005-12-16
two options. 

1. you can VNC into your ubuntu box, then VNC into your XP box from there. You can do this over SSH to you ubuntu box for security if you would like.

2. If it were me and you have a little home router. I would forward port 5901 to the Ubuntu Box and forward port 5902 to the XP box and then just connect to which one you want directly by choosing the port you use.


soule

---

### Post by bingerthedog on 2005-12-16
I do have a router.  The problem I am having I guess is that even without using VNC I can't access my XP machine through Ubuntu using the Network Places.  So even if I am sitting at that machine I can't browse any files on the XP machine.  Is there anything I should check or do to fix this?

---

### Post by soulestream on 2005-12-16
search the forums there are a bunch of howto/help on that

make sure you smb.conf is setup correctly.
make sure XP's firewall is allowing file/print sharing.

soule

---

