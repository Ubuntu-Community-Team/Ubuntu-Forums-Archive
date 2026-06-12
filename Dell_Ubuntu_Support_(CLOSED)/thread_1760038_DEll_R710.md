---
title: "DEll R710"
date: 2011-05-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jeitzen on 2011-05-16
Hello all,

I have a Dell PowerEdge R710.

I can install UEC fine, but after the installation it will not boot into the OS.

I have a 6ir controller... I was reading that there were problems with this controller, but I was under the impression that they had been resolved in an earlier release.

---

### Post by jetole on 2011-06-02
I seem to be having the same issues. I was attempting to install ubuntu 10.04 server on one of the R710 servers I have to setup. I don't have the server (and hence the controller name) in front of me for the disks at the moment but it's a pair of SAS drives on a LSI non raid controller. The issue I ran into is along the lines of a timeout while waiting for the root device at which point, I believe I am returned to the initrd and a busybox prompt. I just came down from the server room to google ubuntu and R710 and this is one of the first sites I found.

P.S.: Sorry for the lack of details on my part. I came down assuming this was a generic issue since I started my install with software raid 1 and LVM but later tried just a auto configure partition with no lvm (as well as various other partitioning schemes) and so far they have all caused the same error after what appears to be a successful install until the first reboot.

UPDATE: My problem was unrelated to the original posters but I will post the details in case someone else with the same issue as mine finds this forum first.

The error I was receiving was "Gave up waiting for root". It then told me that it could not find the virtual device /dev/disk/by-uuid/<insert-your-uuid>. I looked and the device was in fact there. I exited from the initrd/busybox shell and my system continued to boot normally.

I found this is caused by a slow start in the poor man's SAS controllers that Dell gets from LSI which are common in the R series servers from dell. In my case the card was listed as Dell SAS 6 HBA.

I was able to resolve this issue by editing /etc/default/grub and changing the line:
GRUB_CMDLINE_LINUX_DEFAULT="quiet"
to read:
GRUB_CMDLINE_LINUX_DEFAULT="rootdelay=60"

then run update-grub and reboot. This will cause your server to pause before attempting to mount the root device.

More details can be found at [http://goo.gl/lVElC](http://goo.gl/lVElC) regarding this "bug" and the solution.

---

