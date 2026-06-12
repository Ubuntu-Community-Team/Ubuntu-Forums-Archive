---
title: "List DVD drive info command"
date: 2009-02-21
forum: General Help
---

### Post by dolman25 on 2009-02-21
Is there a command for listing CD and DVD drive info like the device number or name its been assigned to i.e., scd0, cdrom, hcd0 or dvdrw. I know there's different ways to find the info like dmesg or look in vlc as I usually do, but is there an easier way.

---

### Post by ajgreeny on 2009-02-21
Usually your cdrom/dvdrom is shown and mounted at /media/cdrom, and it doesn't matter if it is cdrom or dvdrom drive as it is all the same to the system.  It is also shown in the /dev folder as /dev/cdrom, a link to a block device.  Lastly you can find its /dev/sd* notation i your /etc/fstab file ```
cat /etc/fstab
```.     Does this answer your query?

---

### Post by mc4man on 2009-02-21
This will provide a lot of relevant info, if you have a disc in the drive some additional mount info will also be supplied

```
sudo lshw -C disk 
```

---

### Post by dolman25 on 2009-02-22
> **ajgreeny said:**
> Usually your cdrom/dvdrom is shown and mounted at /media/cdrom, and it doesn't matter if it is cdrom or dvdrom drive as it is all the same to the system.  It is also shown in the /dev folder as /dev/cdrom, a link to a block device.  Lastly you can find its /dev/sd* notation i your /etc/fstab file ```
cat /etc/fstab
```.     Does this answer your query?

Are you saying that I could use any of the "cdrom, dvdrom, scd0, dvdrw,"
when using cdrecord command?

---

### Post by ajgreeny on 2009-02-22
I'm not honestly sure but I think the /dev/cdrom from the /dev folder would be the one to use.

---

### Post by dolman25 on 2009-02-23
> **ajgreeny said:**
> I'm not honestly sure but I think the /dev/cdrom from the /dev folder would be the one to use.

When I use growisofs, I use dev/scd0 to burn but in my media it only lists cdrom0.
I think im going to have to experiment with this one, using different dev/.

---

