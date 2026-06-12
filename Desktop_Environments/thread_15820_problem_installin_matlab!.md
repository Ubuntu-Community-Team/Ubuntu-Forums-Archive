---
title: "problem installin matlab!"
date: 2005-02-17
forum: Desktop Environments
---

### Post by lorap on 2005-02-17
i really need this powerfull tool.
i'll be very happy if somebody help me solve this problem.

---

### Post by benjamin on 2005-02-17
Sorry ... I don't understand ...  where is the problem ?

Benjamin

---

### Post by lorap on 2005-02-17
the file named install doesn't run because of permission problem.
it says no permissin for the file.

---

### Post by benjamin on 2005-02-17
[QUOTE=lorap]the file named install doesn't run because of permission problem.
it says no permissin for the file.[/QUOTE]

To set execution permission on a file ... you have to:

chmod +x install

---

### Post by lorap on 2005-02-17
thanks, i'll try this in few minutes.

---

### Post by WW on 2005-02-17
But the matlab install script is on a CD.  You can't change it's permission.

Here's a tip from a different forum:
[http://forum.libranet.com/viewtopic.php?t=2910](http://forum.libranet.com/viewtopic.php?t=2910)

---

### Post by vicent on 2005-03-04
you attempt with:

sh /media/cdrom/install.

The script install was write for sh shell and probably you have used bash.

Perhaps you should be root or sudo for execute install script.

Bye.

---

