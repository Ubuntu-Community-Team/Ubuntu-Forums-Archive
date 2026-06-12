---
title: "Amorak first run wizard and a portable hard drive"
date: 2005-12-04
forum: Desktop Environments
---

### Post by kpm on 2005-12-04
Hi,
I just installed Amorak and was hoping I could keep my music on my USB portable hard drive and not have to copy it over to a location on the local hard dirve... I am given the Linuz directory tree, but there is no sign of my portable hard drive in it.  There is a mnt, but no sign of my Maxtor USB drive... can this be done, or will I need to copy over all those files to my local hard drive??
Thanks

---

### Post by alank on 2005-12-04
Hi, 

I find it best when working with usb devices to keep an eye on the /var/log/messages file so:

in a terminal just for this type:
% sudo tail -f /var/log/messages

This will provide a continuously updating track of kernel messages

Now disconnect or plug in the hard drive usb connection for the first time

you should see lines added in your messages terminal e.g.

=====================================
Dec  5 01:14:15 gauss kernel: [4312165.762000]   Vendor: USB 2.0   Model: Mobile Disk       Rev:
Dec  5 01:14:15 gauss kernel: [4312165.762000]   Type:   Direct-Access             ANSI SCSI revision: 02
Dec  5 01:14:15 gauss kernel: [4312165.765000] SCSI device sda: 251904 512-byte hdwr sectors (129 MB)
Dec  5 01:14:15 gauss kernel: [4312165.766000] sda: Write Protect is off
Dec  5 01:14:15 gauss kernel: [4312165.769000] SCSI device sda: 251904 512-byte hdwr sectors (129 MB)
Dec  5 01:14:15 gauss kernel: [4312165.769000] sda: Write Protect is off
Dec  5 01:14:15 gauss kernel: [4312165.769000]  /dev/scsi/host4/bus0/target0/lun0: p4
Dec  5 01:14:15 gauss kernel: [4312165.772000] Attached scsi removable disk sda at scsi4, channel 0, id 0, lun 0
============================

now type 'mount' to see if your device was mounted automatically, in my example it will be the last line of the results:

==========================
/dev/sda4 on /media/usbdisk type vfat (rw)
========================

In my case the usbkey-drive has been automatically mounted as directory /media/usbdisk

if there is no sign of your device having been mounted you could manually mount it, in  my case:

make a special directory :
% sudo mkdir /mnt/mp3disk

mount the device given the information that you got in messages window:

% sudo mount -t vfat /dev/sda4 /mnt/mp3disk

now you should be able to see files on your portable hard drive if you go to /mnt/mp3disk

I hope this is of some help, 

for more in depth discussion of this look at :
"Mounting USB storage devices and Windows partitions"
found at:
   [http://docs.linux.com/article.pl?sid=04/04/16/1619248&tid=31&tid=7&tid=14](http://docs.linux.com/article.pl?sid=04/04/16/1619248&tid=31&tid=7&tid=14)

Alan.

---

### Post by kpm on 2005-12-04
Thanks,
Yes, I discovered where my usb drive was hiding... /media.

Now I see in Amarok I can point the library in that direction, but can't seem to find a way to do so with RhythmBox... So it looks like Amarok it is!

Thanks again!

---

