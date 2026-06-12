---
title: "How to make a NFS partition be mounted during Ubuntu startup."
date: 2009-03-26
forum: General Help
---

### Post by mmaia on 2009-03-26
Hi,

I have one HD with NFS which has some stuff I allways need. The problem is that always when I turn on Ubuntu I need to manually mount this hd so I can access things on it. 

How do I configure Ubuntu to automatically load this partition during boot time?

The mapping after mount is /media/programs 

and after being mounted works perfectly as expected.( I load some libraries for java developmento from there).

I'm very new to Ubuntu (5 days only) so would be wonderful to have detailed instructions if possible.

tx in advance.
Marcos Maia.

---

### Post by MJWitter on 2009-03-26
Do you mean NFS or NTFS? Is this hard disk in your pc?

---

### Post by nebileix on 2009-03-26
Try this command with alt-f2.

gnome-mount -d /dev/"ur device"

If it can mount on its own, then add the command to System-->Preference-->Sessions.

Else, you got to add the entry to your /etc/fstab.

Cheers..

---

