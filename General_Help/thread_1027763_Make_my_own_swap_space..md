---
title: "Make my own swap space."
date: 2009-01-01
forum: General Help
---

### Post by agim on 2009-01-01
I have two partitions and I want to combine them. What I am planning, is moving all of the data from the right partition to the left partition. Then using Gparted to extend the left partition all the way to the right, to the end of my hard drive. Of course, if I do that, then that partition's swap space will be removed. So I need to add one at the end of the hard drive.
How can I go about doing this the right way?

I am looking and have found several answers online, but I would like some confirmation from someone who has done this before.

Thanks

---

### Post by sdennie on 2009-01-01
When you repartition with gparted, just be sure to create a swap partition somewhere on your disk.  The bottom of this guide tells you how to set it up afterwards (See Troubleshooting): [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq).  It also has information for creating a swap file instead of a swap partition which is another option.

---

