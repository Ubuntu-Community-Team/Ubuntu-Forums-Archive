---
title: "why do we need these folders"
date: 2007-12-27
forum: Dell  Ubuntu Support
---

### Post by manmohanpv on 2007-12-27
Hi Frnds

I recently purchased a dell ubuntu 7.04 system

What is the purpose of these folders?

1. /media/dellutility --what is the usage of this folder? (MS-DOS related files)

2. /media/OS -- what is the usage of this folder? (linux OS image files)

Anybody to help?

-thanks
manmohan

---

### Post by schaumkeks on 2007-12-27
> **manmohanpv said:**
> Hi Frnds

I recently purchased a dell ubuntu 7.04 system

What is the purpose of these folders?

1. /media/dellutility --what is the usage of this folder? (MS-DOS related files)

2. /media/OS -- what is the usage of this folder? (linux OS image files)

Anybody to help?

EDIT: no comment =)

---

### Post by notwen on 2007-12-27
Good chance that these are auto-mounted partitions which happen to be used if you should ever need to restore your PC to like-new status.  You should see an option in GRUB to re-format your PC and re-installing Ubuntu.  Selecting this option would use these 2 partitions in the process.  Unless their partition table has changed since the Feisty 1420n Inspiron this would be my guess.  Check [here]("http://linux.dell.com/wiki/index.php/Wiki_Main_Page") for more info.

---

### Post by gbrainin on 2007-12-27
The partition table for Dell Ubuntu 7.04 machines is shown here: [http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Default_Partitions]("http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Default_Partitions").

Since Linux can see all these partitions, it allows you to mount them if you request (they are not all mounted by default).  /media/dellutility is where Ubuntu will mount the utility partition and /media/OS is where Ubuntu will mount the reinstall partition.

Other than poking around for curiosity, there's no reason to mount either of these partitions.  They are used at boot time for hardware checks and for re-imaging the hard drive, respectively.

---

