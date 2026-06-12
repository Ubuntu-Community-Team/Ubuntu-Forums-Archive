---
title: "Lose XP/Hardy-Load Vista/Jaunty"
date: 2009-07-06
forum: Desktop Environments
---

### Post by AZinOH on 2009-07-06
I have to get rid of Win XP on /dev/sda2 and install Vista. While doing so I intend to get rid of Hardy on /dev/sda5 and replace it with Jaunty. I've never had to do this before, so from what I think I know I need to:

boot the Live CD and use Gparted to delete the existing partitions

format the drive next-yes or no? Will installing Vista do that?

Install Vista

Use the Vista tool to shrink the volume 

Install Jaunty in the 2nd partition

Have I missed anything? Should I do anything differently? Thanks for any assistance.

---

### Post by JC Cheloven on 2009-07-06
No: don't mess with partitions unnecessarily! Simply:

1º Install vista on your existing xp partition. This will wipe xp.
2º Install jaunty on your existing hardy partition. This will wipe hardy and setup the bootloader so you can choose vista at startup.

BTW, are you really interested in vista, which has proven to be terrific? :-D

---

### Post by AZinOH on 2009-07-07
I figured I would change the partitions in order to create a larger Linux partition than I now have (35GB). As far as Vista is concerned, support for an important app that I run for work is being move to Vista and my employer's IT dept will no longer support running the app in XP...that's the main reason for the change. I do run Vista on another machine and while I don't prefer it over XP, I can live with it. Thanks for the reply.

---

### Post by JC Cheloven on 2009-07-07
Ok, you're right: if you want to change sizes of partitions, perhaps is shorter to delete all partitions and build a new scheme from scratch (better than resizing, which takes a lot longer).

---

