---
title: "Running Out Of Disk Space?"
date: 2010-09-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Bikekid450 on 2010-09-21
Hi friends, I got my Ubuntu working again. But now it's saying I have 124.7MB of Disk space, but If I look I have 213GB and 4GB of RAM... What is it on about?

Also if I click on Properties on the File System it says the Ubuntu File is 124GB? 

When I installed Ubuntu I selected the 3GB Installation Size... Was this a mistake? 

Thanks Guys.

---

### Post by mikewhatever on 2010-09-21
Do you have multiple partitions? From Applications->Accessories->Terminal, what's the output of **df -h**  ?

---

### Post by Bikekid450 on 2010-09-21
I'll switch over and check in a sec but the Partition it's installed on, in Windows it shows 213GB free and Ubuntu file is 3.60GB. =/

---

### Post by mikewhatever on 2010-09-21
When installing inside Windows, a certain amount of disk space is allocated to the installation. For example, if you've allocated 5GB, then that's the space Ubuntu is limited to, regardless of how much free space there is on the Windows partition. Makes sense?

---

### Post by Bikekid450 on 2010-09-22
Ahh so selecting the 3gb was a bad idea lol. Can I change this?

---

### Post by Bikekid450 on 2010-09-22
> **mikewhatever said:**
> Do you have multiple partitions? From Applications->Accessories->Terminal, what's the output of **df -h**  ?

 This:  Filesystem            Size  Used Avail Use% Mounted on /dev/loop0            2.7G  2.7G     0 100% / none                  2.0G  380K  2.0G   1% /dev none                  2.0G  240K  2.0G   1% /dev/shm none                  2.0G   84K  2.0G   1% /var/run none                  2.0G     0  2.0G   0% /var/lock none                  2.0G     0  2.0G   0% /lib/init/rw /dev/sdb2             236G  3.8G  232G   2% /host /dev/sdc1             112G  112G  466M 100% /media/FREECOM HDD /dev/sdd1             233G  133G  101G  58% /media/Elements /dev/sde1             466G  121G  345G  26% /media/Muffin

---

### Post by mikewhatever on 2010-09-22
> **Bikekid450 said:**
> Ahh so selecting the 3gb was a bad idea lol. Can I change this?

Yes, but not easily. See the link for more info.
[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?)
If you plan on using Ubuntu, I'd strongly advise a proper installation. The 'inside Windows' thing is basically for evaluation purposes and is not intended from prolonged usage.

---

### Post by goldenbrown on 2010-09-22
Install ubuntu tweak
Back up updates to CD
Run "Package cleanup" in ubuntu tweaks

---

### Post by Elfy on 2010-09-22
> **goldenbrown said:**
> Install ubuntu tweak
Back up updates to CD
Run "Package cleanup" in ubuntu tweaks

While it will make some difference - it's not going to be a huge deal - nor is it permanent.

---

### Post by Bikekid450 on 2010-09-22
Thanks for all your help, I tried to install it by booting from the CD,  with 2 different downloads and 3 different CD's and every time it'd have  an error and corrput my hard drive. But installing it inside Windows XP  works... But about the 3rd time I boot it in Ubuntu it says Ubuntu is  running in Low Graphics mode and won't boot, last 2 times I've  uninstalled it and tried again but this time it seems to have wiped  itself off some how. I'm going to give it one more try, to be honest I'm  getting a little fed up with it now lol I've done everything people  have told me to but my pc just won't have any of it :(

---

