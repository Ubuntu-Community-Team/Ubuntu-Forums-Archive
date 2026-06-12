---
title: "Any advantage to compiling kernel for bioinformatics?"
date: 2007-06-04
forum: Education &amp; Science
---

### Post by Bio Leo on 2007-06-04
I have a Pentium M (2Ghz) machine running Kubuntu (7.04, 32bit) that I'm using for bioinformatics work, mainly local BLAST searches right now.  Its not the fastest thing (I have a search that has been running for 4+ days now), but the budget isn't there for anything better.  I'm wondering if there would be any significant improvement in speed if I compiled a kernel for the 686 architecture rather than just use the stock generic one?  Anyone have any experience with compiling kernels for BLAST or other CPU intensive applications?

---

### Post by halocaridina on 2007-06-04
Hi Bio-Leo,

Unfortunately, I don't anticipate that you would see faster BLAST searches with a custom kernel.  I run a custom kernel on my Toshiba M105 laptop (which is used mainly for bio-info work) and never noticed a speed difference between the stock and custom kernels when it came to BLAST.  FYI, I compiled the custom kernel because 1) I was curious, 2) wanted better suspend/hibernate support under beryl. 

My suggestion for speeding up a BLAST search would be to customize your databases to contain the minimal number of queries that you are interested in.  I find this more efficient then using MPI to spread the search across a cluster.

Hope this helps.

---

### Post by meatpan on 2007-06-05
The major bottlenecks for a string comparison algorithm such as BLAST are likely to be memory and file-system related.   

Here are some suggestions:
Try to get an understanding of the memory and file system demands of your BLAST process by using commands such as top, iostat, and vmstat.   If you find that the BLAST process is not using as much system resources as you want, try adjusting the soft resource limits with the ulimit command.  If you are accessing the data over a network, such as nfs, check performance with nfsstat.  If congestion is evident, consider co-locating your database by copying  it to your local disc.

---

