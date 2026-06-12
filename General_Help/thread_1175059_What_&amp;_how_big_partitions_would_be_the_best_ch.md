---
title: "What &amp; how big partitions would be the best choice for installing Ubuntu ?"
date: 2009-05-31
forum: General Help
---

### Post by ActiveFrost on 2009-05-31
As title says, what partitions I should create, how big they should be ( approximately ) AND, why ( nothing is being done "just for fun" ) ?
Currently I'm doing it in this way :

```
**Mount point**     **Primary/External**     **Type**     **Size**
/               Primary              ext3     10000MB ( 10GB )
/home           Extended             ext3     65000MB ( 65GB )
                Primary              swap     1000MB  ( 1GB )
```

Are these /boot or /usr mount points really useful ( haven't created but saw a few peoples suggesting it ) ?

---

### Post by merlinus on 2009-05-31
Are you wanting to use an external hdd for /home?  Otherwise, your partition sizes seem fine.  I have never had the need for any others.

---

### Post by ActiveFrost on 2009-05-31
> **merlinus said:**
> Are you wanting to use an external hdd for /home?  Otherwise, your partition sizes seem fine.  I have never had the need for any others.

No, actually .. I just wanted to know about which partitions I should or should not create. As I said, saw a few guys saying that I should create another partition for /boot and /usr, but .. I still can't find the reason - why I need them on separate partitions ?
That's what I want to find out .. is it better to keep everything together or to create separate partitions ( /, /home, swap, /usr, /boot, etc. ) :)

---

### Post by merlinus on 2009-05-31
I asked about /home because you had it listed as external.  Perhaps what you were wanting is to create an extended partition to contain /home and swap?

A separate /home will keep your data and application settings intact when installing a new version, or reinstalling the current one.  You choose not to format that partition during the process.

I find that /, /home and /swap are all that I need.  /swap will be created whilst partitioning during install.  Size depends upon system RAM.  I have 4G, and use 1.4G for /swap.

---

### Post by ActiveFrost on 2009-05-31
> **merlinus said:**
> I asked about /home because you had it listed as external.  Perhaps what you were wanting is to create an extended partition to contain /home and swap?

A separate /home will keep your data and application settings intact when installing a new version, or reinstalling the current one.  You choose not to format that partition during the process.

I find that /, /home and /swap are all that I need.  /swap will be created whilst partitioning during install.  Size depends upon system RAM.  I have 4G, and use 1.4G for /swap.

Whoops !! Yes, you are right - /home was meant to be extended, not external ( will fix it ).
About sizes and what's really useful - thanks .. information from "seniors" are always more valuable than a plain text in a dying blog ;)

---

### Post by merlinus on 2009-05-31
FWIW, I would have / in a 10G primary, and then create an extended partition for the rest of the space.  

I would put /home and /swap in the extended one, with /swap at the very end of the hdd.  This will give more flexibility in future should you wish to re-partition /home into one or two smaller partitions.

---

### Post by ActiveFrost on 2009-05-31
> **merlinus said:**
> FWIW, I would have / in a 10G primary, and then create an extended partition for the rest of the space.  

I would put /home and /swap in the extended one, with /swap at the very end of the hdd.  This will give more flexibility in future should you wish to re-partition /home into one or two smaller partitions.

Looks similar to what I've done ! Basically, 10GB primary /, then 1GB of swap ( primary ) at the end of HDD and the rest of space for /home !
Regarding splitting /home into 2 "home's" - I will have 2 home directories or it's just a "trick" for easier file management ?

---

### Post by merlinus on 2009-05-31
What I am suggesting is to put / on the 10G primary partition.  Then make an extended partition using all the rest of the hdd space, and place /home and /swap as logical partitions within the extended partition.

In future you might wish to break up the 65G of /home into one or two additional partitions, for example /art and /data.  It would make backing up the files somewhat easier.

You cannot have more than four primary partitions on an hdd, but can have at least dozens of logical ones in an extended partition.

---

### Post by asmoore82 on 2009-05-31
I'm using 6 GB for Ubuntu's /, another 6 GB for a Fedora /, and the rest for /home
I've only used 70% of the Ubuntu / -
keep in mind that anything you may install in Wine or a Virtual Machine will be on /home.

---

### Post by ActiveFrost on 2009-05-31
> **merlinus said:**
> Then make an extended partition using all the rest of the hdd space, and place /home and /swap as logical partitions within the extended partition.

"Mission Impossible" :D No, really - what you mean by placing /home and /swap as logical partitions ( not really what you mean but how to do that ) ?

> **asmoore82 said:**
> I'm using 6 GB for Ubuntu's /, another 6 GB for a Fedora /, and the rest for /home
I've only used 70% of the Ubuntu / -
keep in mind that anything you may install in Wine or a Virtual Machine will be on /home.

I strictly don't want to return back to Windows XP or any other OS, so .. Wine & Virtual Machines are not my "friends" ( which means 0 bytes ) ;)
Anyway, thanks for the input .. great to see how others are managing their partitions ( keeps us away from trouble ).

---

### Post by merlinus on 2009-05-31
> 
what you mean by placing /home and /swap as logical partitions ( not really what you mean but how to do that ) ?
You can do all this whilst installing by selecting manual at the partitioning screen.  Then set up / as primary, the rest of the disk as extended, and create /home within that.  The partitioner will set up /swap -- you simply tell it what size.

You can use the gparted live cd to set up all the partitions in advance, if so deisred.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Here is a screenshot of my partitions:

---

