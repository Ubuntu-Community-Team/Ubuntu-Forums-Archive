---
title: "fstrim off by default on Desktop editions, why????"
date: 2023-10-27
forum: Desktop Environments
---

### Post by BloodyIron on 2023-10-27
I've had some weird hangs lately, unsure if this is somehow related, but I decided for laughs to execute "sudo fstrim -av" only to find these results:

/mnt/ssd-1tb-0: 261.5 GiB (280830537728 bytes) trimmed on /dev/sdb
/mnt/ssd-2tb-0: 1.2 TiB (1317780197376 bytes) trimmed on /dev/sda1
/boot/efi: 504.9 MiB (529436672 bytes) trimmed on /dev/nvme0n1p1
/: 412.6 GiB (442985697280 bytes) trimmed on /dev/nvme0n1p2

I'm on Ubuntu 23.04 and have been for a good number of months. How is it that NOT ONE of my SSDs had fstrim run against them EVER since install? These are ALL SSD devices.

I went to look at the fstrim service and it looks to have NEVER BEEN RAN.

Why is this the out of the box experience? FSTRIM NEEDS TO BE ON BY DEFAULT. Honestly it should run daily, as the execution time at that rate is extremely low.

---

### Post by TheFu on 2023-10-27
Not everyone has SSDs.  Most of my systems didn't have any SSD until a year ago.
There have been issues running fstrim on some devices with old firmware.
Last time I looked, fstrim was setup to run either weekly or monthly via cron.  I remember reading that using fstrim more often than weekly was bad for an SSD. Perhaps it has changed?  

From the manpage:

```
       Running fstrim frequently, or even using mount -o discard, might  nega&#8208;
       tively affect the lifetime of poor-quality SSD devices.  For most desk&#8208;
       top and server systems a sufficient trimming frequency is once a  week.

```

In theory, running these commands with enable the trim to happen periodically.
```
sudo systemctl enable fstrim.timer
sudo systemctl start fstrim.timer

```

I haven't tested it, so I don't know. In general, I prefer to avoid systemd junk.

---

### Post by BloodyIron on 2023-10-27
1. >99% of new custom or OEM-packaged computers being bought new today use at least one SSD, be it for Windows or Linux.
2. SSDs are now so cheap there is zero reason to not have at least one (and in your particular case I cannot fathom why you waited until last year, but let's put that sample size of 1 aside)
3. The issue isn't the frequency, the issue is it _was not running at all_.

I cannot in good faith _believe_ fstrim was running at all, namely based on the numbers I linked above. It is completely impossible for that much trim to be needed on ALL of those SSDs in just one week. The workload on the example system is nowhere near at the level to warrant that.

I also want to add that fstrim enable results in an output mentioning that it is not designed to start in the same way.

This thread is really meant to engage the developers of Ubuntu, since I am unsure the best place otherwise to post this issue.

---

### Post by TheFu on 2023-10-27
> **BloodyIron said:**
>  
This thread is really meant to engage the developers of Ubuntu, since I am unsure the best place otherwise to post this issue.

Nobody here works for Canonical or systemd teams.  You'll need to go elsewhere for that interaction.  

I just read that newer SSDs automatically trim their storage, so no outside commands are needed.

I didn't have an SSD because I didn't need one. The storage in my systems worked fine, so why change?  I've had a few chromebooks previously. In one of those, the SSD died after a little over 1 yr of use, so I didn't have a good feeling about the quality of SSDs based on my use.  OTOH, my better HDDs were lasting 8-13 yrs. Why change?  In general, I don't like spending money when it isn't required.

---

