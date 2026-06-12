---
title: "Automount fails"
date: 2010-08-29
forum: Desktop Environments
---

### Post by hhoyt on 2010-08-29
Well, I guess it is time to ask for help.

Situation is that NEITHER Linux Mint 9 NOR Ubuntu Maverick will automount my usb or cdrom ??????
I circumvented by manual mounts thru fstab of my usb stick and usb hard drive.

Now I go to burn an iso and find that my cdrom is not detected. 
mount /dev/sr0 /media/cdrom0 does not do the trick, I cannot burn.

What in the world could I have done to my system ?
i think blkid is ok.

Note: Win7 burns the iso to cd just fine. All OS on same CPU (grub2).
I have done some searches but with minimal success.

Thanks, Howard

---

### Post by hhoyt on 2010-08-29
gconf-editor 
media automount open
and
media_automount are both checked.
media_autorun never is not checked.

---

### Post by hhoyt on 2010-08-29
from dmesg:
 1.453910] scsi 1:0:0:0: CD-ROM            TSSTcorp DVD+-RW TS-H653G DW10 PQ: 0 ANSI: 5
[    1.457172] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.457210] Uniform CD-ROM driver Revision: 3.20
[    1.457339] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.457382] sr 1:0:0:0: Attached scsi generic sg1 type 5
and
5262.772800] UDF-fs: Partition marked readonly; forcing readonly mount
[ 5262.802923] UDF-fs INFO UDF: Mounting volume 'New_Disc', timestamp 2009/12/18 18:26 (1f10)
[ 5582.497424] VFS: busy inodes on changed media or resized disk sr0
[ 5595.904388] UDF-fs: Partition marked readonly; forcing readonly mount
[ 5595.934492] UDF-fs INFO UDF: Mounting volume 'New_Disc', timestamp 2009/12/18 18:26 (1f10)

---

### Post by hhoyt on 2010-09-01
n4af@deskpc:~$ tail /var/log/syslog
Sep  1 10:16:42 deskpc kernel: [  431.408672] sd 8:0:0:0: [sdb] Write Protect is off
Sep  1 10:16:42 deskpc kernel: [  431.408685] sd 8:0:0:0: [sdb] Mode Sense: 00 38 00 00
Sep  1 10:16:42 deskpc kernel: [  431.408692] sd 8:0:0:0: [sdb] Assuming drive cache: write through
Sep  1 10:16:42 deskpc kernel: [  431.410523] sd 8:0:0:0: [sdb] Assuming drive cache: write through
Sep  1 10:16:42 deskpc kernel: [  431.410540]  sdb: sdb1 sdb2 < sdb5 > sdb3
Sep  1 10:16:42 deskpc kernel: [  431.414143] sd 8:0:0:0: [sdb] Assuming drive cache: write through
Sep  1 10:16:42 deskpc kernel: [  431.414155] sd 8:0:0:0: [sdb] Attached SCSI disk
Sep  1 10:16:42 deskpc usbmount[2562]: /dev/sdb does not contain a filesystem or disklabel
Sep  1 10:16:42 deskpc usbmount[2592]: /dev/sdb2 does not contain a filesystem or disklabel
Sep  1 10:17:02 deskpc CRON[2688]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
n4af@deskpc:~$ tail /var/log/syslog
Sep  1 10:16:42 deskpc kernel: [  431.408672] sd 8:0:0:0: [sdb] Write Protect is off
Sep  1 10:16:42 deskpc kernel: [  431.408685] sd 8:0:0:0: [sdb] Mode Sense: 00 38 00 00
Sep  1 10:16:42 deskpc kernel: [  431.408692] sd 8:0:0:0: [sdb] Assuming drive cache: write through
Sep  1 10:16:42 deskpc kernel: [  431.410523] sd 8:0:0:0: [sdb] Assuming drive cache: write through
Sep  1 10:16:42 deskpc kernel: [  431.410540]  sdb: sdb1 sdb2 < sdb5 > sdb3
Sep  1 10:16:42 deskpc kernel: [  431.414143] sd 8:0:0:0: [sdb] Assuming drive cache: write through
Sep  1 10:16:42 deskpc kernel: [  431.414155] sd 8:0:0:0: [sdb] Attached SCSI disk
Sep  1 10:16:42 deskpc usbmount[2562]: /dev/sdb does not contain a filesystem or disklabel
Sep  1 10:16:42 deskpc usbmount[2592]: /dev/sdb2 does not contain a filesystem or disklabel
Sep  1 10:17:02 deskpc CRON[2688]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
n4af@deskpc:~$ 

But, of course, Samsung 1TB USB drive  does contain a valid NTFS-3G filesystem.

---

### Post by hhoyt on 2010-09-01
with usbmount removed:

tail /var/log/syslog
Sep  1 10:26:33 deskpc kernel: [ 1022.725130] scsi 9:0:0:0: Direct-Access     SAMSUNG  HD103SI               PQ: 0 ANSI: 2 CCS
Sep  1 10:26:33 deskpc kernel: [ 1022.726078] sd 9:0:0:0: Attached scsi generic sg2 type 0
Sep  1 10:26:33 deskpc kernel: [ 1022.727454] sd 9:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
Sep  1 10:26:33 deskpc kernel: [ 1022.728979] sd 9:0:0:0: [sdb] Write Protect is off
Sep  1 10:26:33 deskpc kernel: [ 1022.728991] sd 9:0:0:0: [sdb] Mode Sense: 00 38 00 00
Sep  1 10:26:33 deskpc kernel: [ 1022.728998] sd 9:0:0:0: [sdb] Assuming drive cache: write through
Sep  1 10:26:33 deskpc kernel: [ 1022.730585] sd 9:0:0:0: [sdb] Assuming drive cache: write through
Sep  1 10:26:33 deskpc kernel: [ 1022.730597]  sdb: sdb1 sdb2 < sdb5 > sdb3
Sep  1 10:26:33 deskpc kernel: [ 1022.735611] sd 9:0:0:0: [sdb] Assuming drive cache: write through
Sep  1 10:26:33 deskpc kernel: [ 1022.735624] sd 9:0:0:0: [sdb] Attached SCSI disk
n4af@deskpc:~$ 

Note, I can manually mount the drive. But automount used to work ?

---

### Post by hhoyt on 2010-09-02
Well, I am going to mark this as solved, tho 'circumvented' might be the better term.

I ended up writing 'automount.rules' to /etc/udev/rules.d
as follows:
ACTION=="add",KERNEL=="sdg*", RUN+="/usr/bin/pmount LABEL=J"
ACTION=="add",KERNEL=="sdg*", RUN+="/usr/bin/pmount LABEL=O"
ACTION=="add",KERNEL=="sdg*", RUN+="/usr/bin/pmount LABEL=N"
ACTION=="remove", KERNEL=="sdg*", RUN+="/bin/umount /dev/sdg1"
ACTION=="remove", KERNEL=="sdg*", RUN+="/bin/umount /dev/sdg3"
ACTION=="remove", KERNEL=="sdg*", RUN+="/bin/umount /dev/sdg5"

I have the removable hd103si (3 partion)usb drive defined to fstab as

#Entry for /dev/sdc1 :
LABEL=J         /media/J        ntfs-3g noauto,locale=en_US.UTF-8       0       0
#Entry for /dev/sdc3 :
LABEL=N         /media/N        ntfs-3g noauto,locale=en_US.UTF-8       0       0
#Entry for /dev/sdc5 :
LABEL=O         /media/O        ntfs-3g noauto,locale=en_US.UTF-8       0       0

The changes seem to allow automount/dismount of the usb hard drive  using pmount and umount. If I use pmount/pumount the mount does not disapear, reason it is done the way it is.

I had also lost automount of my usb stick, but usbmount fixed that.

Howard

---

### Post by linas on 2012-04-01
FWIW, I've got same problem.  A few weeks ago, after a random apt-get update, automounting of USB sticks just stopped working in oneiric.  Arghh. :mad:

In gconf, I found that auto_mount drives and media were both unchecked in the gnome volume manager.  Checking these did not fix anything.

Installing package usbmount from universe fixed it, although the mountpoint changed, and the file manager gui still fails to autorun.

---

### Post by deh on 2012-04-01
I have similar problem.  I gave a friend a USB drive with 11.10 on it.  At some point he found that automount quit working (we don't know the circumstances leading up to this).

This seems to work:

gsettings set org.gnome.desktop.media-handling automount true

The problem he has is that he has to execute that command each time he boots up.  So far I haven't figured how to make it persistent.

---

### Post by Perfect Storm on 2012-04-01
This is an old thread. Please start a new one.


Thread closed.

---

