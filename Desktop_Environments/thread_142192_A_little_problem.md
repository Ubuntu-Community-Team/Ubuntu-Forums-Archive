---
title: "A little problem"
date: 2006-03-09
forum: Desktop Environments
---

### Post by Ko-Pe on 2006-03-09
hello i'm a chilean guy with a little problem.
i have installed ubuntu in a 40 gigs hd, but the space of the swap partition it's really big, it's like 3gigs or someting like that, and i want to know if there's a way to change the amount of space that my swap uses, and if that can be done without formating and re-installing everything.
i have searched in the man pages, and apropos swap and all of that, but it intimidates me a lot. that's my problem in a few words.....
and my justification for changin the swap amount?, i have enough ram (256), and i'm buying some more this or the next weekend, so i think that having that much swap it's more a waste of space than helpfull.
I hope someone can help me with this.
tnxs

---

### Post by Koybe on 2006-03-09
It depends if your are using LVM or not. If so, you can delete yuor swap parition and make another one of... let's say 1Gb. Then you'll be able to add the free volume to a volume group to extend the partition.

Sorry but i don't know exactly how to do it. Maybe you can look for informations on this base.

---

### Post by issueperson on 2006-03-10
in a terminal, type:
---------------------------
sudo apt-get install gparted
---------------------------

that should install the gparted partition manager, which you should be able to access from your applications > system tools menu.  it has a nice graphical interface and is fairly simple to use.

i also don't know if it'll let you delete your swap partition or not while running gdm.

[COLOR="Red"]CAUTION:  be sure you know what you're doing whenever you mess with your partitions.  it's about the easiest way to break your computer that i know of.[/COLOR]

---

