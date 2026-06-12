---
title: "XPS 1530 wifi and HD"
date: 2008-12-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ussndmac on 2008-12-01
Hi All,

I have had my XPS 1530 for a while now. I have also tried a few different version of Ubuntu on it.

A minor issue was when I decided I wanted a fresh install of 8.0.4.
I attempted to install from a live CD and when I told it to format the HD it would only see a few Gb of a 320Gb drive. (It came with Ubuntu from Dell) I booted with Gparted. It saw the whole 320Gb, but 315Gb or so was in windows format (fat16 if I remember). So I just formatted it to exp and away I went.

Was the fat partition there for the Dell recovery stuff?

As for the WIFI in my subject, has anyone been able to get the intel3945 to work with a 802.11b WEP access point?

I've tried 8.0.4, 8.0.10, UbuntuStudio (8.0.4). It did work somewhat with a backport...

Regards,
Mac

---

### Post by jespdj on 2008-12-01
I bought my M1530 with Windows Vista. When it was new, there were four partitions on the harddisk: a small, 100 MB partition with Dell system tools, the Media Direct partition, the Windows partition and a 10 GB partition with recovery stuff. I removed all but the small system utilities partition, and re-installed Windows Vista on a new partition and Ubuntu on another partition. I don't know how important the system utilities partition is; I guess it's a good idea to keep it, for when there's something wrong with your laptop. If you already deleted all the pre-existing partitions and you want them back, then you should be able to reinstall them using the DVDs that you got with your laptop.

I don't know about the Intel 3945 WiFi (I have a 4965 and it works without any problems); there are more people who reported problems with the Intel 3945, so if you search in the forums here you might find some answers on how to make it work.

---

### Post by ussndmac on 2008-12-02
It appears that the 3945 issue has to do with access to a 11b wap. I have not had the chance to try it with anything other than my Linksysy wap and it is 11b only.

I currently have Ubuntu Studio installed. So Dell might have an issue with a support call from me anyway. ;)

Mac

---

