---
title: "Backing up an entire HDD to another HDD"
date: 2006-01-04
forum: Desktop Environments
---

### Post by agds on 2006-01-04
I have two HDDs in my machine.  I'm not using the space on the slave, so I figured I could use it to back up the master.  What's the most elegant way to copy all the data from the master to the slave?  I was considering GParted but thought someone might have a better idea.

---

### Post by encompass on 2006-01-04
that will copy the image itself... you may like to use rsyc... that way you can just back the data that has been saved.  I use that to backup all my data that has changed online.  instead of overrighting EVERYtime ALL your stuff whethere is changed or not... and it can keep your groupd information... that is what makes it better then a strait copy.

---

### Post by teppic on 2006-01-04
If they're exactly the same model and size, you can do a complete clone by using dd (or dd_rescue).

---

### Post by agds on 2006-01-04
Oh, that's too bad.  They're both 80GB but not the same model.  So far it seems like rsync will be the best way.

---

### Post by No_Code on 2006-01-04
I have successfully used dd to backup and restore my Gentoo installation on my laptop before sending it in for service. I knew that it was going to come back wiped with a Windows installation and we all know all of the Gentoo jokes about how long it takes. That little trick also saved my rear one time when I accidently rendered my laptop unable to boot but I had a premade Linux install on another drive.

Anyway, more on dd...

If you do use it to back up a partition, be advised that it copies EVERYTHING, including the free space of the partition. So essentially, if your partition is 80 GB and it's about 25% full, it will consume the entire 80 GB. GParted will trim down the slack space enabling a much smaller image to be stored.

```

dd if=/dev/harddrivecopyingfrom of=/dev/harddrivecopyingto

```

---

### Post by teppic on 2006-01-04
> They're both 80GB but not the same model.

So long as they're both exactly the same size (in bytes) then you should still be able to duplicate them.

An alternative would be to create identical sized partitions and then use dd or dd_rescue to copy the contents of the partitions. That would work on different sized hard drives.

---

