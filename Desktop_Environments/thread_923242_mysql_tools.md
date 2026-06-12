---
title: "mysql tools"
date: 2008-09-18
forum: Desktop Environments
---

### Post by cftaupitz on 2008-09-18
i tried installing mysqlgui tools but i can axtract them etc but they won't work. Any ideas i am new so be gentle lol!!

---

### Post by geovani on 2008-09-18
Preferred system requirements are as follows (for each node) 4 Machines Preferred

    * OS: Linux (Red Hat, SUSE), Solaris, AIX, HP-UX, Mac OS X
    * CPU: 2x Intel Xeon, Intel Itanium, AMD Opteron, Sun SPARC, IBM PowerPC
    * Memory: 16GB RAM
    * HDD: 4x 36GB SCSI (RAID 1 Controller)
    * Network: 1-8 Nodes (Gigabit Ethernet); 8+ Nodes (Dedicated Cluster Interconnect e.g. SCI)

In the 5.1 release, non-indexed columns can be stored on disk and do not require dedicated RAM. However, in 5.0 all indexes as well as all data are still in main memory.

In the 5.1 release, a maximum of 255 nodes can belong to a single MySQL Cluster with up to 48 of those being data nodes. In the 5.0 release the total number of nodes cannot exceed 63. It is possible to change this at compile time, but that has not been thoroughly tested at this point.

geovani

[one time ads]("http://one time ads")

---

### Post by irrdev on 2008-09-18
MySql tools are available in Add/Remove Programs. These packages are modified for Ubuntu, and are garanteed to work. :wink:

---

### Post by dwanders on 2008-09-18
exactly as irrdev said, you should be able to run Add/Remove, or sudo apt-get install mysql-admin mysql-client, or use Synaptic and search for Mysql.

All should work and you dontneedto compile anything - they actually run better and faster than I have seen on Windows (the little Dolphin actually moves on Linux =).

---

