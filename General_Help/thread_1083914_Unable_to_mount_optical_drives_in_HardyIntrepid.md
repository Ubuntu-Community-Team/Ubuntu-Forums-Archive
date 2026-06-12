---
title: "Unable to mount optical drives in Hardy/Intrepid"
date: 2009-03-01
forum: General Help
---

### Post by belg4mit on 2009-03-01
I recently upgraded to Hardy Heron which brought along an updated kernel with the "new and improved" CD interface, but have been unable to mount
discs since. Last night I upgraded to Intrepid Ibex, hoping that things would be better, but alas not.

Whenever I try to mount I get the helpful message :confused::
  mount: Wrong medium type

And the following in dmesg:
  cdrom: pid XXXXX must open device O_NONBLOCK!

The great oracle turns up nothing helpful (and indeed very few entries)
for either.

Output of lshw -c disk:
  *-cdrom                 
       description: CD-R/CD-RW writer
       product: CD-R/RW SH-R522C
       vendor: TSSTcorp
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: TS02
       capabilities: removable audio cd-r cd-rw
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
  *-cdrom
       description: DVD-RAM writer
       product: DVD RW AD-7201S5
       vendor: Optiarc
       physical id: 0.1.0
       bus info: scsi@2:0.1.0
       logical name: /dev/cdrom1
       logical name: /dev/cdrw1
       logical name: /dev/dvd1
       logical name: /dev/dvdrw1
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: 1H0E
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom1

---

### Post by belg4mit on 2009-03-03
Apparently encountered by others as well:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/209076/comments/5](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/209076/comments/5)

I just verified that I could mount an iso9660, but not cdda.
Discs in the rives at boot generate these dmesg:

[   16.039025] end_request: I/O error, dev sr0, sector 0
[   16.039032] Buffer I/O error on device sr0, logical block 0
[   16.039039] Buffer I/O error on device sr0, logical block 1
[   16.039042] Buffer I/O error on device sr0, logical block 2
[   16.039045] Buffer I/O error on device sr0, logical block 3
[   16.040124] end_request: I/O error, dev sr0, sector 0
[   16.040131] Buffer I/O error on device sr0, logical block 0
[   16.208642] end_request: I/O error, dev sr1, sector 0
[   16.208650] Buffer I/O error on device sr1, logical block 0
[   16.208656] Buffer I/O error on device sr1, logical block 1
[   16.208659] Buffer I/O error on device sr1, logical block 2
[   16.208661] Buffer I/O error on device sr1, logical block 3
[   16.214961] end_request: I/O error, dev sr1, sector 0
[   16.214969] Buffer I/O error on device sr1, logical block 0

---

### Post by belg4mit on 2009-03-03
Doh, forgot that Windows' fs view of an audio disc is virtual.
Of course, mount could give a better error...

---

