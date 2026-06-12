---
title: "Home network help: password"
date: 2006-08-03
forum: Desktop Environments
---

### Post by Amorphous_Snake on 2006-08-03
I have 2 PCs, one running Windows XP and acts as an internet gateway, the other runs Ubuntu and receives internet through the other PC.

The internet works fine, but the shared contents have problems. It used to work fine, but now, whenever I want to browse the shared contents on the Windows PC from the Ubuntu PC, I get asked for a password and to select a username and a domain. The same thing happens on the Windows PC when I want to access the Ubuntu one, but this has always been the case, it was never normal.

I am the owner of both PC and no one would change anything in them. Also I don't have problems with the firewall on my Windows PC (McAfee firewall) because, I have internet on the Ubuntu PC and the problem happened even when the firewall is removed. I have the Windows firewall shut down at all times.

Please help, and tell me what happened.

---

### Post by gils0040 on 2006-08-03
sudo gedit /etc/samba/smb.conf
scroll down to 
###AUTHENTICATION###
and uncomment security=whatever
and change it to security=share (or shared i forget)
then restart samba

---

### Post by Amorphous_Snake on 2006-08-05
It's "share", and I tried it and it didn't work.

What shall I do now?

---

