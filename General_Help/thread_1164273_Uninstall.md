---
title: "Uninstall"
date: 2009-05-19
forum: General Help
---

### Post by Jenzuko on 2009-05-19
Hi, I don't know if this is the right place to ask this..
But, how do I uninstall Ubuntu?
I really like it, but it doesn't run right for me for some reason..
I tried deleteing the folder, and the boot screen still stayed and then I couldn't run it at all..
So, how do I uninstall it completly?

---

### Post by ispy on 2009-05-19
assuming you still have your live CD, boot into that, run Gparted and delete the partition Ubuntu is on.

---

### Post by prem1er on 2009-05-19
EDIT: removed post.

---

### Post by jbruced on 2009-05-19
I know he's trying to help, but I think after that you'll have grub problems.

He's right about deleting the partitions using grub(delete swap partition also), but I assume you'll then want to resize windows partition to use all the disk space available.

I needed to get XP to run again a while ago(I don't use windows anymore).
So I booted my XP install disk
chose repair a filesystem
got to a dos prompt
typed fixmbr
rebooted

and XP booted again


DO NOT follow these instructions, it's just what I can remember, find a guide on the forum.

[EDIT] **What folder? You got a wubi install of something?**

---

### Post by growled on 2009-05-19
I think we need a little more information. Do you have Windows installed or do you want to install Windows after deleting Ubuntu, or do you plan on installing something else?

---

### Post by Jenzuko on 2009-05-19
I used my own disc that I downloaded Ubuntu and burned it on there.
I chose swap install so that I could still use Windows, and now I accidently installed TWO ubuntus..
So now 1 ubuntu doesn't work, and the second one is OK.
And I don't have my windows XP disc.

---

### Post by coffeecat on 2009-05-19
Here's some useful information about "uninstalling" Ubuntu:

[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

When you get to the bit about restoring the mbr, use SuperGrubDisk - it's linked on that page. Useful for when you don't have a Windows install disc, and it's much quicker too.

---

