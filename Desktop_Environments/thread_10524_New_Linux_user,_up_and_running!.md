---
title: "New Linux user, up and running!"
date: 2005-01-09
forum: Desktop Environments
---

### Post by tghlk on 2005-01-09
My boss told me he was playing around with ubuntu, and made a bootable CD for me to try out since he liked it so much. I put together an extra computer from scrap and after sorting out some hardware issues, booted the CD and went through the setup. Everything installed fine and after running synaptic for updates, everything is great! heh, being a windows user, I was expecting a reboot...

I'm running a junky PC Chips system board with a PII 400 and 512 meg along with integrated video and a PCI 3com Etherlink III NIC. It connected to my broadband connection with no intervention and even set up the video with no problems. I am quite impressed! It lags a bit, but not bad, and after I learn a tweak a bit, might run better.

Havent found it yet, but is there a lookup chart that shows the comparable linux option for typical windows tasks? Like if I want to check the properties of the hard drive, or want to look at the event viewer, or want to add other user accounts, how do I do it?

I'm an old OS/2 user, so going Linux seems like the most logical step.

---

### Post by fng on 2005-01-09
Add users : Computer -> System Configuration -> Users and groups

Event viewer?
If you are talking about the system monitor : Applications -> System Tools -> System monitor
Or you can open a terminal and just type 'top' (ctrl+c to exit).

Check the properties of the hard drive?
If you wanne see how many free bytes you have left : Open up a terminal and type 'df -h'
```
fng@butters:~ $ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2              18G  2.1G   15G  13% /
tmpfs                 507M     0  507M   0% /dev/shm
/dev/hdc1             190G  102G   89G  54% /mnt/hdc
/dev/hdd1             190G   70G  121G  37% /mnt/hdd
/dev/hde1             153G   25G  129G  17% /mnt/hde
/dev/hdf1              58G  1.4G   56G   3% /mnt/hdf
fng@butters:~ $

```

---

