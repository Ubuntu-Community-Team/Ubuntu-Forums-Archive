---
title: "Backing Up Hard Drive"
date: 2006-02-11
forum: Desktop Environments
---

### Post by josh34 on 2006-02-11
I need to reinstall Windows, but I can't boot into Windows to back up my data. I have run some tools and I can see that my data is still on the drive. My question is, how can I backup the contents of this hard drive to another hard drive? I have an Ubuntu live CD, so I use that to execute backup software. Also, once Windows is reinstalled, I will need to retrieve some of the backed up files and put them back on the Windows hard drive.

Thanks,
Josh

---

### Post by eriefisher on 2006-02-11
Is this a dualboot machine or are you just using the live cd to rescue windows?

eriefisher

---

### Post by josh34 on 2006-02-11
I am just using the live CD to rescue Windows. I have Ubuntu installed on it's own computer.

Thanks,
Josh

---

### Post by eriefisher on 2006-02-11
From the live cd you should be able to mount the drive and then copy all the files to a cd or usb stick. I just saw a how-to here to mount NTFS, do a search its right here somewhere.

eriefisher

---

### Post by josh34 on 2006-02-11
Could I connect my 60GB spare hard drive, boot the live cd, format the backup drive, mount the NTFS partition and then copy the files?

Thanks,
Josh

P.S. What format should I format the 60GB backup drive with?

***Update***
I copied all of the files from my windows drive to the backup drive, formated in Fat32. Is there anyway that I can boot from these files, or do I need to reinstall windows. And if I do need to reinstall windows, will this backup drive be recognized in my computer?

---

### Post by ardchoille on 2006-02-12
You can use a LiveCD, like SystemRescueCD, to image a partition and then you can burn the image to a CD/DVD. System Rescue CD is a very nice LiveCD that has partimage and lots of other tools. You can download, and find docs for, System Rescue CD here: [http://www.sysresccd.org/](http://www.sysresccd.org/)

---

