---
title: "Flyback"
date: 2009-01-06
forum: General Help
---

### Post by elkade on 2009-01-06
Hope I'm in the right area.

Am unable to initiate a manual backup.  When I click on back up now, this is what I get:

External Storage Location Error
You do not appear to have write access to your external storage location, or the location does not exist.

I have used this storage for backups before, now all of sudden I get this.  Am perplexed, don't understand.

The external storage is a 750 gig Seagate using a USB connection.  
My OS is Intrepid.  There is 400 gig of free space available.

Help

Larry

---

### Post by thedarkwinter on 2009-01-06
Hi

it is possible that you have written to the backup disc using sudo/root privelages, and that you can not overwrite that data as a user.

you can try changing the ownership of all the files on the disk by typing into the terminal:

chown -R username:username /media/usbdisk (where /media/usbdisk is the mount point)

cheers,
michael

---

### Post by elkade on 2009-03-30
> **thedarkwinter said:**
> Hi

it is possible that you have written to the backup disc using sudo/root privelages, and that you can not overwrite that data as a user.

you can try changing the ownership of all the files on the disk by typing into the terminal:

chown -R username:username /media/usbdisk (where /media/usbdisk is the mount point)

cheers,
michael

No, I initiate the app as a user.  Will look and see if there have been any updates, as I do like the app and what a backup looks like when done.

---

