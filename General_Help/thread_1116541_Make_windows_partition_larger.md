---
title: "Make windows partition larger"
date: 2009-04-05
forum: General Help
---

### Post by chougard on 2009-04-05
My friend is trying to make his windows partition larger and his ubuntu partition smaller. We managed to change the ubuntu partition to 10gb but can't add the free space to the windows partition. I have attached a screenshot of what gparted looks like right now.

Thank you for any help!

---

### Post by bodhi.zazen on 2009-04-05
You do not need to resize the Ubuntu partition, you have plenty of free space.

You have to resize the extended partition , sda2

You also need to do this in steps

resize sda2 -> apply changes
resize your windows partition

If the free space is not adjacent to your windows partition, after resizing sda2, you will need to move the partitions, adding yet another step. Again, one step at at time and aply changes before going to the next step.

---

### Post by chougard on 2009-04-05
It wont let him resize sda2 to anything under 46744mb. The current size is 46932mb.

---

### Post by bodhi.zazen on 2009-04-05
You need to unmount the swap partition first. The live CD mounts the swap partition automatically.

```
sudo swapoff -a
```

---

### Post by chougard on 2009-04-05
He still isn't able to lower the size of sda2.

---

### Post by bodhi.zazen on 2009-04-05
Are you running from a live CD ? Did you turn swap off ?

If so, then you probably need to move or delete the swap partition (and ada5) so that all the unpartitioned space it on the left of sda2

So sda2 will look like this :

... sda2 ...
| <-- Unpartitioned space (free space) --> | <-- sda5 --> | <-- swap --> |

You may also find the gparted on ling guide helpful.

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

---

### Post by chougard on 2009-04-06
Thank you!

---

