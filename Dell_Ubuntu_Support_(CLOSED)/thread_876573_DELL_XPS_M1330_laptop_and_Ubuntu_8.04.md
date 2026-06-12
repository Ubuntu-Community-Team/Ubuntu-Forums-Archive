---
title: "DELL XPS M1330 laptop and Ubuntu 8.04"
date: 2008-07-31
forum: Dell Ubuntu Support (CLOSED)
---

### Post by n00blar on 2008-07-31
Does this mix support wireless?
I've read several threads that talk about Ubuntu 7.10 supporting wireless on this laptop, but I've just installed 8.04 and it seems that the wireless card is not even recognize.
Do I have to use the older version of Ubuntu to get wireless working on this laptop?

Thanks.!

---

### Post by akniss on 2008-07-31
Well, that depends... which wireless card do you have?  The Intel 4965 and 3945 are both recognized by ubuntu.  If you chose one of the Dell wireless options, it might not work as well.

---

### Post by n00blar on 2008-07-31
lspci reports

09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

So, it's a Broadcom then.

---

### Post by n00blar on 2008-08-01
Ok, so I guess I need to ask how to get the Broadcom wireless card working with Ubuntu. It appears that Ubuntu doesn't have drivers for this wireless card.

Any suggestions?

---

### Post by muteXe on 2008-08-01
No problems with my dell xpsM1330 regarding wireless.
Dunno if that's any help?

mute

---

### Post by n00blar on 2008-08-01
The wireless problem appears only if you have a broadcom wireless card. Those laptops with Intel wireless cards do not have these issues.

---

### Post by n00blar on 2008-08-01
I found the a fix for the wireless problem [here]("http://ubuntuforums.org/showthread.php?t=297092&highlight=BCM4328").

This HOWTO works for Ubuntu 8.04 and a DELL XPS M1330 with a broadcom wireless card.

---

