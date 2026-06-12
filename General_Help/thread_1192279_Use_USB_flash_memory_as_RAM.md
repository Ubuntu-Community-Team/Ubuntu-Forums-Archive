---
title: "Use USB flash memory as RAM"
date: 2009-06-19
forum: General Help
---

### Post by acablue on 2009-06-19
Is it possible to use a flash drive as extra RAM in Linux? Is there a program out there for that?

---

### Post by SerenityKill3r on 2009-06-19
It's possible if you could program it, but it would be pointless, because USB is much much much slower than DDR2/DDR3 memory.

---

### Post by jenkinbr on 2009-06-19
You'd be better off setting up a swap partition on a physical harddisk rather than using USB media.

Aside from that, it is possible, but I'm not sure how.

---

### Post by s3a on 2009-06-20
Format your USB flash drive as a swap partition by going to System-->Administration-->Partition Editor. However, as previously mentionned, you should either upgrade RAM or create a swap partition on your physical hard drive.

---

### Post by dcstar on 2009-06-20
> **acablue said:**
> Is it possible to use a flash drive as extra RAM in Linux? Is there a program out there for that?

That is probably the best way known to severely shorten the life of any SSD device.

It is basically so mindless that only an organisation with a short-term focus would even support it, BTW this sort of thing is used on Windows, innit?    ;)

---

### Post by brawnypandora0 on 2011-03-21
I have 512MB DDR1 RAM on my laptop. If I use two 1GB USB flash drives, how much faster would it make my laptop? Would it feel like 2.5 GB RAM?

---

### Post by idoitprone on 2011-03-21
> **brawnypandora0 said:**
> I have 512MB DDR1 RAM on my laptop. If I use two 1GB USB flash drives, how much faster would it make my laptop? Would it feel like 2.5 GB RAM?

Never, ram is so much faster than usb drives. It might make your computer slower

[http://superuser.com/questions/146192/is-usb-ram-or-a-usb-processor-a-feasible-concept](http://superuser.com/questions/146192/is-usb-ram-or-a-usb-processor-a-feasible-concept)

---

### Post by mcduck on 2011-03-21
> **brawnypandora0 said:**
> I have 512MB DDR1 RAM on my laptop. If I use two 1GB USB flash drives, how much faster would it make my laptop? Would it feel like 2.5 GB RAM?

As fast as it's now, and *much* slower if the system at some point actually runs out of RAM and starts using the USB drives. :D

Flash memory and hard drives have nowhere near the transfer speeds of RAM memory. They can be used to store data that doesn't fit into RAM, but that's simply to allow the computer to do tasks that it couldn't do otherwise, not to improve performance. (The process is caled "swapping" ans it's something you really, really want to avoid if possible. It makes things horribly slow.)

---

### Post by jerome1232 on 2011-03-21
RAM access time is measured in nanoseconds. 
USB flash drive access time is measured in milliseconds.

If I remember correctly there's 1,000 nanoseconds in a millisecond.

Does that give you an idea of the difference? And why swapping is slow, particulary thrashing?

AFAIK virtual memory is never a direct replacement for physical memory, the information still has to end up in physical memory to be used by the processor, so the ram "swaps" some of it's information and grabs the information in virtual memory.



As an aside the only reason Windows does this I believe is to get the page file off the c drive, your primary drive. This minimizes fragmentation and the fact that swap is on a separate device ought to speed things up a notch.

---

