---
title: "Very slow resonse in Ubuntu"
date: 2009-06-15
forum: General Help
---

### Post by pumber on 2009-06-15
MY PC is running Ubuntu hardy. In these few days, the system was very slow. After logging in , it's normal. However, after about 10 seconds, it became very slow. It makes me feel the machine is hang.

What's wrong ?
How to fix it ?

Thank you!

---

### Post by lavinog on 2009-06-15
Lots of times there are progams that will run in the background that will slow down your computer. Scrollkeeper has been a problem in the past.
A good way to tell is to open up the terminal and use top.
it will show you all the processes and the cpu usage.
htop has a slightly nicer interface, but is not installed by default, you can install it with ```
sudo apt-get install htop
``` or [Click here to install it with synaptic](apt:htop)

---

### Post by pumber on 2009-06-20
These are the errors shown when I shut down the PC.

Can anyone help to figure out the problem ?

Thank you !

---

### Post by paperplate9 on 2009-06-20
> **pumber said:**
> These are the errors shown when I shut down the PC.

Can anyone help to figure out the problem ?

Thank you !

Your hard drive is bad.

---

### Post by pumber on 2009-06-20
So, any way  to avoid writing the data in the bad sector ???

and anyway to clone my hard disk to another one ?

Thank you !

---

### Post by Soul-Sing on 2009-06-20
You could do a fsck.

---

### Post by paperplate9 on 2009-06-20
Yup, boot from a CD, then do a fsck on the drive (if this is the drive that has your root partition).

---

### Post by pumber on 2009-06-21
I got the following message 

[PHP]fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext2 :   &#35037; &#32622; &#25110;&#31995;&#32113;&#36039;&#28304;&#24537;&#30860;&#20013; while trying to open /dev/sdb
Filesystem mounted or opened exclusively by another program?[/PHP]

What can I do ?

The Chinese words means" [COLOR="Red"][COLOR="Red"]device or system resources is busy[/COLOR][/COLOR] "

---

### Post by paperplate9 on 2009-06-21
Did you boot from CD? The error is because fsck doesn't want to mess with a mounted partition.

---

### Post by pumber on 2009-06-21
Yes, i boot it from CD.

What can I do  now ?

Thank you!

---

