---
title: "Folder Synchronization"
date: 2009-01-23
forum: General Help
---

### Post by Patricrawley on 2009-01-23
I have a 4 GB USB flash drive and this is more than enough to store all of my school documents on it and I would like to be able to synchronize the two when I plug in the Flash drive. IS there anyway to do this? I want to have my ~/Documents/School folder sync up with my /media/SANUSB/School folder as soon as it's mounted.

---

### Post by HereInOz on 2009-01-23
I am not sure of a way to make it automatic, but perhaps a script which runs rsync would do the job.

You could first run rsync to copy new and changed files from the USB drive to your hdd, then reverse the procedure for any files on the hdd which are not existing on the usb drive.

The only question that would arise is, what to do with files on one drive which you have deliberately deleted from the other one.  They would automatically be recreated in a two way copy such as this.  

If, however, it was only a one way copy, from the USB drive to the hdd, then you could use the -delete switch to get rid of any files on the hdd which you had deleted from the USB drive.  Or you can not use the -delete switch and any files you delete from the USB drive will be maintained on the hdd until you manually delete them.

Sorry I can't offer a more seamless option.

---

### Post by Patricrawley on 2009-01-23
That's fine, where would I put the scrpit?

---

### Post by hyper_ch on 2009-01-23
you could try unison as it's bidirectional synchronizing... never used it though.

---

