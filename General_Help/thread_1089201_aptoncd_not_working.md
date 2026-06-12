---
title: "aptoncd not working"
date: 2009-03-06
forum: General Help
---

### Post by kask1984 on 2009-03-06
hi every body ,my problem is when i am trying to use aptoncd, it is not working .welcome window appears displaying with optioins create and restore.when i click create it reads package information ,when it comes to around 65% window automatically closes.
earlier i used   aptoncd.
i am using ubuntu 8.10 and intel processor
i tried these things
----->restarted system but not worked
----->removed and added aptoncd also not working
help me
thanks

---

### Post by dcstar on 2009-03-06
> **kask1984 said:**
> hi every body ,my problem is when i am trying to use aptoncd, it is not working .welcome window appears displaying with optioins create and restore.when i click create it reads package information ,when it comes to around 65% window automatically closes.
earlier i used   aptoncd.
i am using ubuntu 8.10 and intel processor
i tried these things
----->restarted system but not worked
----->removed and added aptoncd also not working
help me
thanks

Do you have sufficient disk space in your root partition?

---

### Post by kask1984 on 2009-03-06
i have 8.7GB free space

---

### Post by 4Orbs on 2009-03-06
Aptoncd worked for me after I un-checked the "create metapackage" option.

---

### Post by kask1984 on 2009-03-06
where i have to un check the "create metapackage" option.

---

### Post by 4Orbs on 2009-03-07
My mistake, that option doesn't appear until after all the packages have been listed. But I did have the same problem as yours, the first step would reach 99% and then close. After several attempts, it finally worked. Not sure what really fixed it, but it might be because I reverted to the default setting of my Home folder as where the new iso would be written and saved. The first time (when it crashed) I was trying to save the iso file in folder located on a different partition of the HDD.

---

### Post by dcstar on 2009-03-07
Try deleting the (hidden) .aptoncd folder in your home drive.

---

### Post by kask1984 on 2009-03-07
post #7 is not working any other ideas please

---

### Post by dcstar on 2009-03-07
> **kask1984 said:**
> post #7 is not working any other ideas please

Does starting Synaptic work correctly?

---

### Post by kask1984 on 2009-03-07
yes it worked correctly

---

### Post by kartiksinghal on 2009-03-09
I am also having the same problem of AptonCD automatically closing itself in the middle of adding packages. This problem occurs when there are sufficiently large no. of archived packages in the apt cache.

I have figured out something:
I observed the System Resources using the System Monitor and found out that while adding packages in AptonCd the amount of RAM usage increases dramatically and it crashes when the usage is almost 96%. Maybe there is some bug with the software itself. I have 1.5 GB RAM which is more than the 1.3 GB archives I have but it doesn't work even if I remove some packages and make the archive size down to around 700 MB.

---

### Post by robinparriath on 2009-03-14
Hi everyone,

The same problem was fixed in my system when I did a clean install of the aptoncd_0.1.98-0ubuntu4_all, available from:

[aptoncd_0.1.98-0ubuntu4_all.deb]("http://launchpadlibrarian.net/18476205/aptoncd_0.1.98-0ubuntu4_all.deb")

It is a gdebi install.(Just double click on it after downloading to start installation)

Please note that this is not available from the Ubuntu repositories and hence considered 'fix in progress'... but it works with Ubuntu 8.10 Interpid Ibex(that's my system).

To read the original thread discussing this bug on launchpad, visit:
[URL="https://bugs.launchpad.net/aptoncd/+bug/272509"]Bug#272509
[/URL]

---

### Post by kask1984 on 2009-03-16
thanks it's working

---

