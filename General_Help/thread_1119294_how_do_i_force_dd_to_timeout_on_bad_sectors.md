---
title: "how do i force dd to timeout on bad sectors"
date: 2009-04-07
forum: General Help
---

### Post by lavinog on 2009-04-07
I have a hd that lost was damaged a couple of years ago. Back when I was using windows I was able to recover some data from it, but at 1MB/hr...after a month of working with it I gave up and put it in storage.
I happened to give it a try with linux this time. I see some potential for using the dd command to create a disk image, then use photorec to do the recovery.
with dd I can get some data, but every 1000 sectors it hits a group of bad blocks. It will wait for about a minute before moving on. Is there a way to get dd to not wait so long before moving on?
I am thinking about using a loop to get dd to transfer about 1000 blocks (should take less than a sec), using another thread, wait 1 sec, if dd didn't complete kill it and adjust the dumpfile position...before I do this I was wondering if there was an easier way.

---

### Post by bumanie on 2009-04-07
Try ddrescue  - it's in the repo's. It skips bad sectors and keeps going and tehn comes back to try to read the bad sectors again when finished the rest. ddrescue is also useful if there is a power outage or something at logs where it is up to and continues from where it was interrupted. > sudo apt-get install ddrescue

---

### Post by lavinog on 2009-04-07
Thanks for the info, I will give that a try.

---

### Post by bumanie on 2009-04-07
Hope it works :)

---

### Post by lavinog on 2009-04-07
on a side note: This seems to be a lot easier with a multi-core processor...a bad sector causes a 100% on one core.

---

### Post by lavinog on 2009-04-07
It does simplify the process a bit, but the problem is still that it spends too much time on bad sectors.
also, both dd and dd_rescue don't respond to ^c in a timely manner either, which means they will not respond to a kill signal anyway, so it looks like I am stuck with just spending some time on it.
I still like the dd_rescue...It handles the book keeping for me...so I can jump around the disk.

---

### Post by dcstar on 2009-04-08
> **lavinog said:**
> It does simplify the process a bit, but the problem is still that it spends too much time on bad sectors.
........

The time spent for a storage device to return a read error is (I am almost certain) coded in the device itself.

The dd (or whatever) application is basically putting a disk IO request to the kernel which then puts it into a queue and sends the request to the appropriate device. The kernel then has to wait for the response and if it is a bad-block read situation, then the disk itself will go through various procedures (retries, remapping to a "spare" sector etc) making every effort to deliver the data before returning a status to the kernel which then passes that on to the application.

There may be a way of telling the disk drive to reduce the default quantity of retries to speed things up a bit, but I am not aware of how this might be done.

---

### Post by lavinog on 2009-04-08
> **dcstar said:**
> 
There may be a way of telling the disk drive to reduce the default quantity of retries to speed things up a bit, but I am not aware of how this might be done.
Good point

found setting in hdparm:
```
-D     Enable/disable the on-drive defect management feature, whereby the drive firmware tries to automatically manage  defective  sectors  by  relocating  them  to
              "spare"  sectors  reserved  by  the factory for such.  Control of this feature via the -D flag is not supported for most modern drives since ATA-4; thus this
              command may fail.

```
I might try that out.

---

