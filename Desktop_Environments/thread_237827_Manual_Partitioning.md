---
title: "Manual Partitioning?"
date: 2006-08-16
forum: Desktop Environments
---

### Post by Mike_N on 2006-08-16
I've dual booted my desktop with two hard drives before, no problem. But i just got a laptop with a 60 gig drive, already partitioned in half. I want to maually partion the 2nd partion for Ubuntu but i'm not sure exactley how to or what size to make each of the three partitions(root, swap, home). I have about 25 gig to work with here...?

Thanks, Mike

---

### Post by jordilin on 2006-08-16
> **Mike_N said:**
> I've dual booted my desktop with two hard drives before, no problem. But i just got a laptop with a 60 gig drive, already partitioned in half. I want to maually partion the 2nd partion for Ubuntu but i'm not sure exactley how to or what size to make each of the three partitions(root, swap, home). I have about 25 gig to work with here...?

Thanks, Mike

Swap is generally your ram*2. Your root partition should be enough with 9 Gb or less, depending of how many software you are planning to install. All the rest for your home.

---

### Post by lagagnon on 2006-08-16
To add to the above post it is generally accepted that it is usually ram*2 up to a maximum of 512MB for swap - unless you run a HUGE number of applications and games all at once. Most folks with 1GB of RAM rarely, if ever, use their swap, so having 2GB of swap is a complete waste of space. For normal workstation usage 512MB of swap is more than enough.

---

### Post by Mike_N on 2006-08-16
That was very helpful but... After setting those partitions, i was prompted to assign 4 places, not 3(root,home,swap). It wanted me to assign either Usr or Boot to a partion that is part of my Win setup...

So close, can anyone answer that part for me? Thanks, Mike

---

### Post by ezsit on 2006-08-16
> I've dual booted my desktop with two hard drives before, no problem. But i just got a laptop with a 60 gig drive, already partitioned in half. I want to maually partion the 2nd partion for Ubuntu but i'm not sure exactley how to or what size to make each of the three partitions(root, swap, home). I have about 25 gig to work with here...?

You should use the partitioner to delete the DOS/Windows partition at the end of the drive to make space for Linux partitions. I would suggest keeping it simple and create a 512MB swap partition at the beginning of free space and create / partition on the rest of the drive. As a beginner, there really is no need to separate out /boot, /home, or /usr.

If you really want to create multiple partitions, I would suggest 512MB swap, 256MB /boot, 12GB /, and the rest for /home.

> After setting those partitions, i was prompted to assign 4 places, not 3(root,home,swap). It wanted me to assign either Usr or Boot to a partion that is part of my Win setup...

I'm not clear on what exactly is going on here. Is this the suggestion from the installer? If so, you do not have to follow the advice, you are free to do as you please.

---

### Post by randell6564 on 2006-08-16
What installation disk are you using?  If you already partitioned your HD, then ubuntu should recognize the free space and act accordingly. (she should partition the free space automatically)

You should not have to worry about how much space to allocate to the free partition.

---

