---
title: "sudoers file corrupt"
date: 2006-01-31
forum: Desktop Environments
---

### Post by pjdg on 2006-01-31
Oke I was playing with sudoedit to see how it worked.
When finished I set the file back to its original state. Atleast I tought I did.
But now if I try to sudo I am getting the messages 

>>> sudoers file: syntax error, line 20 <<<
sudo: parse error in /etc/sudoers near line 2

The problem is I also get this when I am trying to do sudoedit. Which means I don't know how to correct this.

I tried to boot from a live cd (Knoppix) but my etc directory is in a LVM partion which I don't know how to mount.

Any suggestions on how to solve this would be apperciated.

---

### Post by kaamos on 2006-01-31
Can you select the "recovery" option in grubs menu? That should get you root access.

---

### Post by jrib on 2006-01-31
[QUOTE=pjdg]Oke I was playing with sudoedit to see how it worked.
When finished I set the file back to its original state. Atleast I tought I did.
But now if I try to sudo I am getting the messages 

>>> sudoers file: syntax error, line 20 <<<
sudo: parse error in /etc/sudoers near line 2

The problem is I also get this when I am trying to do sudoedit. Which means I don't know how to correct this.

I tried to boot from a live cd (Knoppix) but my etc directory is in a LVM partion which I don't know how to mount.

Any suggestions on how to solve this would be apperciated.[/QUOTE]

I don't use lvm but I think you mount what is in /dev/mapper/, but kaamos' method is probably easier.  here is my sudoers by the way: [http://paste.ubuntu-nl.org/7021](http://paste.ubuntu-nl.org/7021)

---

