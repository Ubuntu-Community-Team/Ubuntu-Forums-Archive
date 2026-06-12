---
title: "Syncing USB Disk"
date: 2009-03-18
forum: General Help
---

### Post by jdavis on 2009-03-18
I currently have 2x1TB drives in my machine, mirrored as RAID1. I recently purchased another 1TB drive, which sits in a USB enclosure. I have backed up all of my data to this drive (so I have 3 backups, and so that I can take the data with me if necessary) and now want to write a small shell script using rsync or similar which will keep the USB backup drive in sync with the RAID array.

Essentially I just need the script to copy over any new files to the USB which have been created on the RAID drive, and remove any files which have been deleted from the RAID disks.

Can anyone suggest a nice little command that will achieve this?

thanks, Jonathan

---

### Post by prince_niceguy on 2009-03-18
hmm... interesting... i too did something like this but i was runnig the command manually, you can configure to have it run at specific time... the command is as givien below.

```

rsync -r -t -v --progress --delete "/data/" "/mnt/disk1/data/"

```

replace the folder name with the folder name you want to sync...

actually if it is raid1 then why not include that too as part of raid... every thing will get copied everywhere... may be not possible... will have to do some research on it...

---

