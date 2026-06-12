---
title: "Sharing an Audio CD via NBD"
date: 2008-12-28
forum: General Help
---

### Post by marco_vermeulen on 2008-12-28
Hi all,

I hope someone can help me with my problem (or otherwise tell me off because I'm crazy!)

I have two linux boxes. My server box is running Intrepid. This machine has a cdrom drive that I want to share with my client box as a Network Block Device. My primary purpose is to rip CDs across a network he he he (can that even be done?!?)

I've set up NBD on my server box with the following config in /etc/nbd-server/config:
```

[generic]
# If you want to run everything as root rather than the nbd user, you
# may either say "root" in the two following lines, or remove them
# altogether. Do not remove the [generic] section, however.
	user = nbd
	group = nbd

# What follows are export definitions. You may create as much of them as
# you want, but the section header has to be unique.
[export]
	exportname = /dev/cdrom
	port = 2000
```

I initialize NBD:
```
/etc/init.d/nbd-server start

```

Then on my client side, i run the following command:
```
nbd-client thirdcross 2000 /dev/nbd0
``` (thirdcross being my server box)

I get the following message appearing:
```
Negotiation: ..size = 476068KB
bs=1024, sz=476068
Kernel call returned: File existsClosing: que, sock, done

```

Here's the problem: when I try accessing this block device through my favorite ripper, abcde, I get the following error message:
```
cd-discid: /dev/nbd0: CDROMREADTOCHDR: Invalid argument
[ERROR] abcde: CD could not be read. Perhaps there's no CD in the drive?

```

It feels like I'm really close, but seem to be up against a wall. Can anyone help me? Please!
Cheers,
Marco.

---

### Post by jimsmithkka on 2009-04-15
i am having a similar problem, i am trying to share a raw disk over NBD to a nother system, not a partition but an entire disk, and i get it hanging on Negotiation:

Other posts say that the partition needs to be shared, not the disk itself, so you might try finding the /dev/ file for the cd's partition (if it has one) then try connecting to it.

As for my problem i want to group a bunch of hdds from a few systems in on LVM to be used as a single, large virtual HDD, and i am stuck at that point 

if anyone else has any input on it, it would be appreciated

---

