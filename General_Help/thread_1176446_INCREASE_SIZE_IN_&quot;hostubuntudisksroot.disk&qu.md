---
title: "INCREASE SIZE IN &quot;/host/ubuntu/disks/root.disk&quot;"
date: 2009-06-02
forum: General Help
---

### Post by luisridaocruz on 2009-06-02
I run into a problem trying to install ORACLE under Ubuntu.
One of the reasons was the lack of memory available to set it up.
I copy-paste the filesystem disk usage:

Filesystem            Size  Used Avail Use% Mounted on
/host/ubuntu/disks/root.disk
                       13G   11G  1.8G  86% /
tmpfs                 989M     0  989M   0% /lib/init/rw
varrun                989M  120K  989M   1% /var/run
varlock               989M     0  989M   0% /var/lock
udev                  989M  172K  989M   1% /dev
tmpfs                 989M     0  989M   0% /dev/shm
/dev/sda1              61G   32G   29G  54% /host
lrm                   989M  2.7M  987M   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sdb1             233G  162G   72G  70% /media/New Volume
/dev/sda2              89G   43G   47G  49% /media/Data

As seen there is a lot of space available in /dev/sdal1 from which I wish to move some gigabytes to /host/ubuntu/disks/root.disk.
Is this possible?

Thanks in advance

---

### Post by dcstar on 2009-06-03
> **luisridaocruz said:**
> I run into a problem trying to install ORACLE under Ubuntu.
One of the reasons was the lack of memory available to set it up.
I copy-paste the filesystem disk usage:

Filesystem            Size  Used Avail Use% Mounted on
/host/ubuntu/disks/root.disk
                       13G   11G  1.8G  86% /
tmpfs                 989M     0  989M   0% /lib/init/rw
varrun                989M  120K  989M   1% /var/run
varlock               989M     0  989M   0% /var/lock
udev                  989M  172K  989M   1% /dev
tmpfs                 989M     0  989M   0% /dev/shm
/dev/sda1              61G   32G   29G  54% /host
lrm                   989M  2.7M  987M   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sdb1             233G  162G   72G  70% /media/New Volume
/dev/sda2              89G   43G   47G  49% /media/Data

As seen there is a lot of space available in /dev/sdal1 from which I wish to move some gigabytes to /host/ubuntu/disks/root.disk.
Is this possible?

Thanks in advance

If you know where Oracle is being installed you can simply make a Soft Link from a folder in /host to replace that folder on the root drive (assuming /host is a Linux filesystem).

---

