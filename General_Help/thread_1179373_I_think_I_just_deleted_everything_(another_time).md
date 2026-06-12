---
title: "I think I just deleted everything (another time)"
date: 2009-06-05
forum: General Help
---

### Post by Harry2 on 2009-06-05
okay, last time it was only windows deleted...
So I put in the install disk, tried installing a 4 keys didnt work....

So I come onto ubuntu to msn and get help then all of my data (100gigs+) has been deleted/dissappeared...

I cannot find the drive called 'data' (which it was before) and I have check sda1,2 and 4. 3 says "You must specify the filetype system"

What can I do and would you need anything to help?

---

### Post by Harry2 on 2009-06-05
So its deleted :'(
Windows deleted it this time :(

[http://i44.tinypic.com/34pf8s7.png](http://i44.tinypic.com/34pf8s7.png)

Anyway of getting this back?

---

### Post by blueridgedog on 2009-06-05
From the live CD install/run test disk and see if it can see the missing partition.

Install with:

```
sudo apt-get install testdisk
```

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

A howto is here (scroll down):

[http://www.users.bigpond.net.au/hermanzone/p21.html](http://www.users.bigpond.net.au/hermanzone/p21.html)

---

### Post by Harry2 on 2009-06-05
> **blueridgedog said:**
> From the live CD install/run test disk and see if it can see the missing partition.

Install with:

```
sudo apt-get install testdisk
```[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

A howto is here (scroll down):

[http://www.users.bigpond.net.au/hermanzone/p21.html](http://www.users.bigpond.net.au/hermanzone/p21.html)

But I cant get onto an installed version of ubuntu (it keeps booting to windows configuration)  so just booting from cd atm and that means I cant install

---

### Post by blueridgedog on 2009-06-05
Can you burn another image from another system?  Here is a version of Ubuntu with the tools included:

[http://ubuntu-rescue-remix.org/](http://ubuntu-rescue-remix.org/)

---

