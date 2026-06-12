---
title: "Accidentally deleted a partition"
date: 2009-05-22
forum: General Help
---

### Post by SPQRobin on 2009-05-22
Hello,

*I didn't know where to post my question, so if this is not appropriate for ubuntuforums.org, please refer me to a better forum or website.*

So, I had these partitions: 

[LIST=1]
[*]ntfs (C:\) with Vista
[*]ntfs (S:\) with misc stuff, mainly images
[*]ext3 with ubuntu
[/LIST]
I had some problems with my sound on ubuntu so I reinstalled ubuntu, but I accidentally reinstalled it on my 2nd partition (yes I know, how stupid!). ](*,)
Of course, I want to recover my images, but, how can I do this? I could reset my 2nd partition as ntfs to recover them, or find good software that recovers data from ext3, or something else...?
I haven't done anything yet because I don't want to do something wrong (I already recovered all pictures from my camera, so the most recent ones are at least back!).

What should I do?

---

### Post by VMC on 2009-05-22
> **SPQRobin said:**
> 
[*]ntfs (S:\) with misc stuff, mainly images
... want to recover my images, but, how can I do this? I could reset my 2nd partition as ntfs to recover them, or find good software that recovers data from ext3, or something else...?
I haven't done anything yet because I don't want to do something wrong (I already recovered all pictures from my camera, so the most recent ones are at least back!).

What should I do? So the "S" drive that was once NTFS FS is now Ext3?
I'm not sure if moving it back to NTFS will help.
But first try Testdisk and see if it can find anything.

Also look it this link it has some photo recover program:
[http://www.linux.com/news/enterprise/storage/8257-how-to-recover-lost-files-after-you-accidentally-wipe-your-hard-drive](http://www.linux.com/news/enterprise/storage/8257-how-to-recover-lost-files-after-you-accidentally-wipe-your-hard-drive)

Good luck.

---

### Post by SPQRobin on 2009-05-23
> **VMC said:**
> So the "S" drive that was once NTFS FS is now Ext3?
Indeed.

> **VMC said:**
> But first try Testdisk and see if it can find anything.

Also look it this link it has some photo recover program:
[http://www.linux.com/news/enterprise/storage/8257-how-to-recover-lost-files-after-you-accidentally-wipe-your-hard-drive](http://www.linux.com/news/enterprise/storage/8257-how-to-recover-lost-files-after-you-accidentally-wipe-your-hard-drive)
Thanks, I'll try them and hope it works.

---

### Post by SPQRobin on 2009-05-23
PhotoRec is running, and the first images are being recovered! :D

I had a few very large text files on that partition, and now they are appearing in *lots* of small text files.

Anyway, thank you!

---

