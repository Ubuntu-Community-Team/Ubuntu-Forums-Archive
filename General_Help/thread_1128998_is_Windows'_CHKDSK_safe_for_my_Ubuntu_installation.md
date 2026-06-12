---
title: "is Windows' CHKDSK safe for my Ubuntu installation?"
date: 2009-04-18
forum: General Help
---

### Post by Ceiling Fan Man on 2009-04-18
Sorry if this might seem like a dumb question... I've been having slow HDD problems lately and errors popping up when booting Ubuntu (I'm running on a Seagate Barracuda 7200.11, so that worries me), so I was going to run FSCK... But being a newbie to Linux, I haven't figured out how to do that yet. Then I started to run CHKDSK from WinXP, but came across a post from someone else who claimed that CHKDSK had deleted GRUB... So my questions are: 

Was that a fluke and I can actually safely run CHKDSK?

Is there a way to check my EXT3 partition besides FSCK that might be easier for a Linux beginner to understand?

I'll check back in about 10 hours -ish (Bedtime for me). Thanks in advance.

---

### Post by juancarlospaco on 2009-04-18
EXT auto-check itself.

Defragment Windows partitions.

---

### Post by drs305 on 2009-04-18
You can 'schedule' an fsck check for the next boot by running this command in terminal:
```
sudo touch /forcefsck
```
If you wanted to check a partition that is not your system partition, change to that partition first and then run the command. For instance, if you wanted it to check sda6, which was mounted on /media/test, you would:
```

cd /media/test
sudo touch /forcefsck

```

---

### Post by Ceiling Fan Man on 2009-04-18
> **drs305 said:**
> You can 'schedule' an fsck check for the next boot by running this command in terminal:
```
sudo touch /forcefsck
```
If you wanted to check a partition that is not your system partition, change to that partition first and then run the command. For instance, if you wanted it to check sda6, which was mounted on /media/test, you would:
```

cd /media/test
sudo touch /forcefsck

```

Awesome, that's simple enough... Much easier to understand than what I found by Googling... I found instruction for like booting into single user mode and have your install disc ready and booting into Live CD and all kinds of stuff. Thank you Drs305.

I'll just use FSCK instead of CHKDSK, but I'm still curious if CHKDSK really does wipe out GRUB? Anybody know?

---

### Post by matrixblue on 2009-04-18
I've had a system with a Ubuntu/XP dualboot and ran CHKDSK many times and it's never occured. This not to say that it's impossible but unless I think CHKDSK focuses on the partition and not the entire disk.

I would avoid commands like fixmbr though.

If it ever happens to you use the Supergrub boot disk to re-install grub.

---

### Post by Ceiling Fan Man on 2009-04-18
> **matrixblue said:**
> I've had a system with a Ubuntu/XP dualboot and ran CHKDSK many times and it's never occured. This not to say that it's impossible but unless I think CHKDSK focuses on the partition and not the entire disk.

I would avoid commands like fixmbr though.

If it ever happens to you use the Supergrub boot disk to re-install grub.

Thank you for the input. I'll definitely look into Supergrub.

---

