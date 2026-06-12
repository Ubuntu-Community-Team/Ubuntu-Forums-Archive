---
title: "Testdisk help and really BAD hard drive problem"
date: 2009-06-17
forum: General Help
---

### Post by hurbie on 2009-06-17
Hi everyone!

I don't know much about computers so bear with me please. 
Here's my problem:
I had windows xp and there were too much problems to the point it became impossible to use my laptop. The blue screen kept popping up and I no longer could boot at this point. I erased the hard drive and put ubuntu. In doing so I erased the partition and lost all my data of course. But well now I can use my laptop. 
I found this program called Testdisk to see if I can retrieve so deleted stuff. When I run testdisk there seems to be so bad problems: the problems say : ```
warning: incorrect number of heads and cylinders
``` and after doing a deeper search and when wanting to do "P:list files", I get : ```
can't open filesystem. filesystem damaged
```. I need to note also I ran testdisk with the option "no partition".

My understanding is that such problems are related to the geometry of the disk and I need to modify that and solve the problems so I can check the old partitions. I am posting here the screenshots of gparted and testdisk:
Can someone solve my problem so I can try to retrieve any lost data? What operation should I do to correct the geometry of the disk?
[IMG]http://img36.imageshack.us/img36/263/gparted.png[/IMG]


[IMG]http://img29.imageshack.us/img29/908/testdisk1.png[/IMG]


[IMG]http://img188.imageshack.us/img188/889/testdisk2.png[/IMG]

I interrupted testdisk because it was taking too long: here's the end result (it was still under the option "no partition")

[IMG]http://img140.imageshack.us/img140/9200/testdisk3.png[/IMG]

and that too:

[IMG]http://img4.imageshack.us/img4/1387/testdisk4.png[/IMG]
Thanks for any help!

---

### Post by hurbie on 2009-06-17
I apologize for the big pictures.
Here's the screen shot for testdisk with the option "intel"

[IMG]http://img504.imageshack.us/img504/2217/inteltestdisk.png[/IMG]

---

### Post by grantemsley on 2009-06-17
If you have installed Ubuntu on the same drive as windows was on, it has already overwritten most of the data.  Very few programs will be able to recover and data, and ones that can probably won't find very much.

---

### Post by hurbie on 2009-06-17
> **grantemsley said:**
> If you have installed Ubuntu on the same drive as windows was on, it has already overwritten most of the data.  Very few programs will be able to recover and data, and ones that can probably won't find very much.

Thank you for your answer!

Do you know by any chance how I can solve those "heads and cylinder" problems?
Thx

---

### Post by grantemsley on 2009-06-17
No, I've never used that program.  I just tested it on my system and it didn't report any errors.

---

