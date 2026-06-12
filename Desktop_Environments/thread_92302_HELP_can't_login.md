---
title: "HELP can't login"
date: 2005-11-19
forum: Desktop Environments
---

### Post by megashake on 2005-11-19
HELP! have recommended ubuntu to a good friend so we are trying to setup a dual boot winddows/ubuntu 5.10 notebook, ubuntu installation goes ok but during the installation we get prompted for the user setup and after we enter the users' actual name and then user name and password the process starts all over again and just keeps looping

1. Enter the user's actual name
2. Enter the user name
3. enter the password

..and then it starts again... :( :( :(
 
we tried finishing the installation and during the process we received an error prompt about an empty password field and of course we try to specify the password over and over again and if we ignore this proceedure we get to the login prompt and cannot login...

Am on the 3rd installaton now, the only difference is that I made the swap partition logical and not primary and when I entered in the users detail it just continued as normal but then it got to about 80% of the full installation and then died..

Is there a way to set or apply the password via command prompt if you either have not correctly applied the password or have forgotten it? This of of course is the root or sudo so without that you cannot login at all :(

---

### Post by iguanaphobic on 2005-11-19
How big is the / partition that you are trying to install to??

How big is the swap partition?

---

### Post by UbunuAndrew on 2005-11-19
Just out of curiousity; Opposed to doing the partitions yourself, have you 'tried' letting Ubuntu perform this task itself? Technically you shouldn't have too many problems doing this manually, providing you're using standard partitioning schemes or smart ones anyhow. It wouldn't hurt to see if it will autopartition, and work - that will limit it down to your partitioning.

---

### Post by megashake on 2005-11-19
I wanted to create a shared FAT32 partition on a 60GB HD

10GB Primary Part, NTFS (XP) 
100MB logical Part, /boot
5GB Logical Part, ext3 (ubuntu)
40GB Logical Part, FAT32 
512MB Logical Part, swap

Someone advised me to make the swap partition primary but that seemed to cause problems.
Should the swap partition be before are after the FAT partiton?

The machine in question has 512MB DDR 333MHz RAM so perhaps a swap partition isn't needed, my own machine has 1GB DDR 333MHz RAM

---

### Post by UbunuAndrew on 2005-11-19
Just out of personal experiance.. ALWAYS use a SWAP. Mind you that's just a personal pref. I would also suggest you 'always' using double the RAM for the swap amount. Therefore, the machine in question should have 1024mb swap.

---

