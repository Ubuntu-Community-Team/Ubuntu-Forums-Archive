---
title: "Ubuntu &quot;microwulf&quot; -- slave node configuration"
date: 2009-04-04
forum: General Help
---

### Post by marpha on 2009-04-04
I am trying to put together a Ubuntu-based beowulf cluster [_based on the design_]("http://www.calvin.edu/~adams/research/microwulf/") of a Professor Adams at Calvin.

Our system hardware is very similar to theirs, consisting of four nodes each with a dual core chip.  The slaves each have one onboard and one PCI-express gigabit card.  The head node has an addition NIC to connect outside.

We've followed the directions closely and have (what seems to be) working DHCP, PXE, and TFTP.  Booting the slaves provides messages implying the kernel is loaded.

Our problem seems to be in mounting our nfs drive.  We get the following error:

[INDENT]Retrying nfs mount
Running /scripts/nfs-premount...
Done
rpc failed 2[/INDENT]

Does anyone know what this means and/or where we might be going wrong?  (We are complete newbies to networking and really linux in general...)

We thought maybe we need to add nfs-common to the slave system, but this doesn't seem to be a problem for anyone else and furthermore, it's not clear to us how we'd apt-get on a system that can't boot!  Any suggestions on that?

---

### Post by cariboo on 2009-04-04
Have you got nfs-kernel-server installed on each of the modes?

Jim

---

### Post by marpha on 2009-04-04
Jim,

We've got nfs-server on the head node. Do slave nodes need nfs-server?  I thought they would need nfs-common as clients.

If one or the other nfs package is needed, is there a way to install it on the slave's system without being able to boot the slave?  i.e. is there some way to install packages on non-boot partitions?

---

### Post by d1ngd0 on 2011-05-05
i was having a similar problem. it turned out that my second card was also trying to boot though I have no idea why. so I currently have it disconnected.

also to install something onto a node i used the following

sudo chroot /nodes/nfs/nodeX /bin/bash

/nodes/nfs/nodeX being the path to the mounted drive the node runs off.

then...

sudo apt-get install ...

---

