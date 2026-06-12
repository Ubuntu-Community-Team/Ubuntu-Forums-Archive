---
title: "unused/available disk space issue.."
date: 2009-02-04
forum: General Help
---

### Post by vrv123 on 2009-02-04
Hi Experts,

This is a question long due, I have ubuntu 8.10 on my dell xps m1330, and thats the only OS on it, so entire partitioned disk is allocated to ubuntu.

I see that the available free/unused disk space is at variance when i compare properties of diskusage analyzer, system monitor & gparted/grub, respectively.

please have a look at the jpg attached to see the storage differences as marked in red.

the extended sda2 and swap sda5 have their own allocations of 8.69 gb each, I feel that is correct. so in reality, I would like to have the unused space of 217.58 in the system, as shown correctly in the gparted.

Can anyone tell me which property should i trust the most,
df command or diskusage analyzer or system monitor or gparted/grub

and why are these tools showing different sizes at the first place ?
is this normal or a bug ?

as a tech guy myself, I would like to see system memory and space allocations to be in sync across the board...

Thanks in advance!

---

### Post by mb_webguy on 2009-02-04
I think that the problem is primarily that a GB isn't necessarily a GB.  Hard drive manufacturers use the technically correct definition of a GB, which is one billion (1000^3 or 10^9) Bytes.  However, when dealing with computers, it's generally more convenient to deal with powers of 2, so by convention, a GB usually means 1024^3 (or 2^30) Bytes.  There's an IEEE standard that tries to clear up this confusion by calling a binary GB a GibiByte (abbreviated GiB), but the field has been slow to adopt the standard.

If you'll notice, System Monitor is reporting a total capacity of 206.4 **GiB**, while GParted is reporting 224.20 **GB**, which if you do the math is pretty close to being equivalent.  I'm not sure about the number reported by DUA, but if I had to guess, I'd say that this is indeed in GB, and it is the actual partition size minus space reserved by certain special system files and directories.

---

### Post by jerome1232 on 2009-02-04
I can say for one thing I'm not sure what that first page in System Monitor is reading because it's way off if it's meant to measure total file system capacity. (In my case)

I suppose the first page could be excluding things mounted under /media.

---

### Post by vrv123 on 2009-02-04
Thanks for the reply webguy. nice explanation for gb/gib.

but I beg to differ on the gb display.
you mentioned: "If you'll notice, System Monitor is reporting a total capacity of 206.4 GiB, while GParted is reporting 224.20 GB"

but in my screenshot it shows as "gib" in both gparted & system monitor, respectively. 
only the dua shows "gb".

I am little confused as user jerome1232, why are the numbers different, why can't the source reflect the "df -h" on the tools properties.
the non-tech savvy ubuntu users will surely get confused.

any ideas ?

---

### Post by mb_webguy on 2009-02-04
> **vrv123 said:**
> but in my screenshot it shows as "gib" in both gparted & system monitor, respectively. 
only the dua shows "gb".

*blink blink*  Huh.  You're right.  I misread it.  Well, the numbers still work out.  A GB is about .93 of a GiB, and 206 is roughly .93 of 224...  

Ok.  Now I'm confused.  

The answer is that the different applications use different units of measurement, and may exclude certain parts of the filesystem.  Try "df -h" in the terminal.  That's going to give you the most accurate results (which I think will probably correspond to the numbers in GParted).  You'll notice that there are several things listed under your home directory such as tmpfs and varrun which I think are being excluded from DUA and System monitor.

---

### Post by vrv123 on 2009-02-04
Yep, I always issue a df command to get the real numbers.
but it is the gui toolset that confused me a little bit.

I have always trusted(& will trust) unix/linux(ubuntu), the only thing i am paranoid about is that ubuntu kernel should not mismanage my free/available space and hence display wrong data.  

guess its just allocated that way.

---

### Post by mb_webguy on 2009-02-04
There's also the matter of filesystem overhead.  The actual size of a partition is going to be larger than the usable space, because of various aspects of the file system itself, such as file permissions.  The df command and GParted show actual size, while DUA and System Monitor are showing usable space, I think.  And I think DUA is excluding certain parts of the filesystem (such as those listed by df) excluded by System Monitor.

All of them are accurate, I think.  They're just measuring different things...

---

### Post by vrv123 on 2009-02-04
webguy, thanks for the clarification and all your replies!

conclusion: "df" command, as always, is a reliable buddy.

---

