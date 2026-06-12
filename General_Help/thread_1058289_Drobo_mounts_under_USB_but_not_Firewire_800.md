---
title: "Drobo mounts under USB but not Firewire 800"
date: 2009-02-02
forum: General Help
---

### Post by kcavagnolo on 2009-02-02
I've had a Drobo for a while and it works great under Ubuntu. I want to switch from using the USB 2.0 interface to the Firewire 800 interface, but when I hook the Drobo up, sudo lshw returns:

     *-scsi:0
          physical id: 1
          bus info: firewire@001a620283420446
          logical name: scsi11
        *-disk
             description: SCSI Disk
             product: Mass Storage
             vendor: TRUSTED
             physical id: 0.0.0
             bus info: scsi@11:0.0.0
             logical name: /dev/sde
             version: 2.00
             serial: 0DC083420446
             size: 2TiB (2199GB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=6d4c7db9-860f-40a7-9ea4-b1f7ed05ed13
           *-volume UNCLAIMED
                description: Data partition
                physical id: 1
                bus info: scsi@11:0.0.0,1
                serial: 7543fe24-fb70-4347-a4d5-64928a1bb343
                capacity: 8191GiB
                configuration: name=ext2

I've tried many transformations in /etc/fstab to mount the drive, but nothing is taking. Anyone have any ideas?

---

### Post by kcavagnolo on 2009-02-04
Hmmm... I think the firewire card is not being recognized by the system...

From lspci:
03:00.0 FireWire (IEEE 1394): Agere Systems Unknown device 5901 (rev 06)

This is odd because this chipset is known to work with ubuntu 8.04.

And the raw1394 dev is being created by udev...

Anyone have an idea?

---

### Post by aquamammal on 2009-03-08
I‘m planning on getting a Drobo myself. Hopefully people can solve this problem~

---

### Post by lindude on 2009-08-31
I'm having a similar problem but using firewire 400. I just reformatted my Drobo to a 4tb lun, (ntfs), and it won't load via firewire but it will via USB.

I can see  it via firewire using the drobo dashboard, (all its functions seem to work), but the drive doesn't mount so I cant access it to read and write files to.

Any ideas?


As a side note. I use to have a 2tb lun and when I first tried my firewire cable, (and a few more time a various intervals), I had the same problem it just wouldn't mount, so i only used the USB cable, But yesterday when delete a whole heap of file so there was basically nothing on it the firewire cable started to work.

---

### Post by lindude on 2010-05-18
Firewire 400 works in 10.04 but is slower than usb2.

---

