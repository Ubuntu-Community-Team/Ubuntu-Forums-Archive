---
title: "CD ROM problems... not auto mounting...EDGY"
date: 2009-01-04
forum: General Help
---

### Post by tiger.woods on 2009-01-04
I'm having problems with my CDROM its not automounting and doesn't seem to want to manually mount either.

The drive does exist on /dev/hdb, this is from dmesg:

[   24.702224] hdb: _NEC DVD_RW ND-2510A, ATAPI CD/DVD-ROM drive

I could use some expert help on this one...

Thanks,

---

### Post by Slim Odds on 2009-01-04
EDGY is dead.

Upgrade to at least HARDY.

---

### Post by niteshifter on 2009-01-04
Hi,

What version isn't going to matter with the OP's problem. It shouldn't matter at all. If the OP wants to run Edgy, let him run Edgy. This whole GNU/Linux thang is about freedom of choice ... you want conformity with the masses, use a MS product.

Now back to the OP: When you try a disk in the drive (auto or manual mount) does dmesg show anything?
```
dmesg | tail
```

---

### Post by Slim Odds on 2009-01-04
> **niteshifter said:**
> What version isn't going to matter with the OP's problem. It shouldn't matter at all. If the OP wants to run Edgy, let him run Edgy. This whole GNU/Linux thang is about freedom of choice ... you want conformity with the masses, use a MS product.

Upgrading to a **supported** release might just fix the problem. I don't see the need to fight with old stuff....

The OP can use whatever they want. Install Redhat 5.2 for all I care. I think that you take the whole "freedom of choice" to an absurd end.

I suggested an LTS release so that they will get a larger window of time to get possible fixes to whatever problems they may have.

---

### Post by tiger.woods on 2009-01-04
> **niteshifter said:**
> Hi,

What version isn't going to matter with the OP's problem. It shouldn't matter at all. If the OP wants to run Edgy, let him run Edgy. This whole GNU/Linux thang is about freedom of choice ... you want conformity with the masses, use a MS product.

Now back to the OP: When you try a disk in the drive (auto or manual mount) does dmesg show anything?
```
dmesg | tail
```

I'm actually not going to respond to Slim Odds... its a useless point he can go help someone else.

This is what I see from dmesg tail nothing related to the CDROM or DVD drive. I do have it set to automount and browse the media when a Cd is inserted.

[870162.957088] floppy0: obsolete eject ioctl
[870162.957094] floppy0: please use floppycontrol --eject
[871596.906101] end_request: I/O error, dev fd0, sector 0
[871596.930084] end_request: I/O error, dev fd0, sector 0

---

### Post by Slim Odds on 2009-01-04
> **tiger.woods said:**
> I'm actually not going to respond to Slim Odds... its a useless point he can go help someone else.

Whatever dude. It was intended to be helpful

> **tiger.woods said:**
> 
[870162.957088] floppy0: obsolete eject ioctl
[870162.957094] floppy0: please use floppycontrol --eject
[871596.906101] end_request: I/O error, dev fd0, sector 0
[871596.930084] end_request: I/O error, dev fd0, sector 0

You're gonna need more tail. Try at least 30 lines.

---

### Post by tiger.woods on 2009-01-04
> **Slim Odds said:**
> Whatever dude. It was intended to be helpful

You're gonna need more tail. Try at least 30 lines.


Maybe its just how it was presented... since you were posting a reply I assume that you meant to help..

Anyway I went ahead with great hesitation and did an upgrade luckily it seemed to have gone without a hitch and the CD now works...

Is there a kernel version that is deployed by Hardy by default?

Thanks,

---

### Post by mc4man on 2009-01-04
This is my current one (hardy-updates

> doug@doug-desktop:~$ uname -a
Linux doug-desktop 2.6.24-22-generic #1 SMP Mon Nov 24 18:32:42 UTC 2008 i686 GNU/Linux


---

### Post by Slim Odds on 2009-01-04
> **tiger.woods said:**
> Maybe its just how it was presented... since you were posting a reply I assume that you meant to help..

Anyway I went ahead with great hesitation and did an upgrade luckily it seemed to have gone without a hitch and the CD now works...

Is there a kernel version that is deployed by Hardy by default?

Thanks,

Glad that worked out for you.

I'm sorry that some people take those short posts wrong, but I was just trying to make it short and simple.

Edgy and Feisty are no longer supported and it's much better to get on an LTS release if you don't want to upgrade often. (NOTE: even Gusty will "expire" in April, which isn't far away).

My kernel is also:```
Linux 2.6.24-22-generic #1 SMP Mon Nov 24 18:32:42 UTC 2008 i686 GNU/Linux

```

---

### Post by tiger.woods on 2009-01-05
> **Slim Odds said:**
> Glad that worked out for you.

I'm sorry that some people take those short posts wrong, but I was just trying to make it short and simple.

Edgy and Feisty are no longer supported and it's much better to get on an LTS release if you don't want to upgrade often. (NOTE: even Gusty will "expire" in April, which isn't far away).

My kernel is also:```
Linux 2.6.24-22-generic #1 SMP Mon Nov 24 18:32:42 UTC 2008 i686 GNU/Linux

```

Many thanks for the help and information... at least I'm current on the kernel..

TW,

---

