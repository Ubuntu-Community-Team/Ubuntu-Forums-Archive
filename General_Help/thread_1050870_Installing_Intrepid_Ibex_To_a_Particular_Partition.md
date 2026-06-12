---
title: "Installing Intrepid Ibex To a Particular Partition"
date: 2009-01-26
forum: General Help
---

### Post by Shravet on 2009-01-26
Hi 
I have an Injtrepid Ibex DVD and wish to install it to a particular primary partition,/dev/hda2,on my HDD,which I have created specially for Ubuntu.(I alredy have XP Sp2 installed and want to set up a dual boot).I want to know if I install it to that Partition will the swap Partition be automatically be craeted as a Logical Partition within /dev/hda2. If yes, then will there not be any problems given that I already have a large extended Partition containing 3 Logical Partitions.
My partitioning scheme is:
C:--Primary (22.5GB)
G:--Primary (/dev/hda2)(16.5GB)
D:--Logical (39GB)
E:--Logical (39GB)
F:--Logical (31GB)

I hope that clears up the picture.
Trouble is I want to install Ubuntu to /dev/hda2 only as I have quit a lot of Data residing on E: and F: and dont wish to undergo hte pain of backing uo and restoring data as a result of installing Ubuntu to a Logial Partition or for that matter creating a new Partition altogether.
Thanks

---

### Post by weblordpepe on 2009-01-26
I don't see the problem really. Your should be fine, dude. The partition editor during setup will let you install anything on anything.

Ya wont be the first person to put ubuntu onto a machine with existing partitions :)

---

### Post by overlord.gaurav on 2009-01-26
> Trouble is I want to install Ubuntu to /dev/hda2 only as I have quit a lot of Data residing on E: and F: and dont wish to undergo hte pain of backing uo and restoring data as a result of installing Ubuntu to a Logial Partition or for that matter creating a new Partition altogether.

As mentioned above..it ain't no trouble. Just go ahead with the install and when then partitioner loads up..select 'Manually edit partition table'. Now select the desired partition with mount point as "\" and you're done !

---

### Post by Shravet on 2009-02-10
Thanks a Lot both you guys I appreciate your help:)

---

