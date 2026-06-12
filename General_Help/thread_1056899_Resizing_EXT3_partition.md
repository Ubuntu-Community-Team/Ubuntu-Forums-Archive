---
title: "Resizing EXT3 partition"
date: 2009-02-01
forum: General Help
---

### Post by arepaking on 2009-02-01
Hello experts,

I need to resize my EXT3 /home partition to be able to allocate more space. I attached a screen shot from Gparted that shows my current partition structure and information.

Basically, I have a Primary partition called sda3 that needs to be deleted and inserted in sda2 -> EXT3 -> /home partition ( also known as sda9 which is a logical partition). By running the LiveCD I am able to delete sda2 and make it appear as unallocated but I cannot move or assign it to sda9.

Does anyone knows how to properly achieve this? my ultimate goal is to merge sda9 (home logical partition) with sda3 (Primary Partition that I intend to delete and reassign).

Thanks you very much in advance,
AK

---

### Post by meindian523 on 2009-02-01
Please confirm which of sda2 or sda3 you want merged with your /home partition(sda9).sda2 is an extended partition which CONTAINS your sda9 partition and attaching it to sda9 is impossible unless you reinstall.sda3 is a primary partition which makes sense as the partition you want to merge with your /home(sda9)

---

### Post by arepaking on 2009-02-01
> **meindian523 said:**
> Please confirm which of sda2 or sda3 you want merged with your /home partition(sda9).sda2 is an extended partition which CONTAINS your sda9 partition and attaching it to sda9 is impossible unless you reinstall.sda3 is a primary partition which makes sense as the partition you want to merge with your /home(sda9)

Hi, Thanks for your quick reply. I corrected a typo in my first post. I would like to delete sda3 so I can take that free space into sda9. Please note that sda9 is inside the extended partition sda2.

Thanks again,
AK

---

### Post by meindian523 on 2009-02-01
exactly.After deleting sda3,you need to backup your /home,and resize(using Partition Editor(aka GParted) in System>>Administration) sda2 to take the newly unallocated space.Then you have to resize your logical partition sda9 to take the newly unallocated space,which is now within sda9.

Or,for a simpler way,you could format sda3 as ext3 or something and mount it under some folder in /home.Like you could make it your Movies partition,and mount it under /home/<username>/Movies or something.That will just involve editing /etc/fstab.

---

### Post by arepaking on 2009-02-01
Thanks for confirming the proper way to do this. I will make these changes and I will report the results to the community.

Wish me luck!

---

### Post by arepaking on 2009-02-01
_Reporting Results:_
I tried two methods and the results goes as follows:

a) Using Ubuntu Live CD: when the desktop appeared I ran Gparted but I notice that sda2 got mounted for some reasons. This unable me to make any changes to sda9. Results-> [COLOR="Red"]Failed[/COLOR]

b) Using Gparted Live CD: I was able to see all the partitions unmounted and it was very easy to make the changes. Results -> [COLOR="Green"]Success[/COLOR]

Now, there is one more change that I need to do get my partitions sorted out. The file attached to this post shows my new partition structure and information.

sd6 and sda9 belongs to the extended partition sda2. I need to shrink sd6 to free at least 50GB and allocate that space to sda9. I tried to do this while I was using GParted Live CD but even though I am able to shrink sda6 to the proper size, I cannot allocate the freed space to sd9. How can I move the unallocated space to the end of the partition so sd9 can grow?

Thank you very much for all your support.

Kind Regards,
ArepaKing

---

### Post by caljohnsmith on 2009-02-01
I just thought I would mention that when you run gparted from the Live CD, usually you can easily unmount any mounted partition by right-clicking the partition within gparted and selecting "unmount". But to try and answer your question, your sda6 and sda9 partitions have sda7 and sda8 between them, so if you shrink sda6, you would have to move both sda7 and sda8 to the left to free up space before the sda9 partition, and then you could expand sda9 to use that space. Since you want to shrink sda6 at least 50 GB, instead of actually moving sda7 and sda8, it might be faster to copy both those partitions to the freed space you will have after shrinking sda6. Once you are done copying them there, you could mount the newly-copied sda8 partition (whatever it will be called) to make sure it is intact, and once you've confirmed that, you could delete the original sda8. And there's not much to worry about with sda7 since it is just swap, so after copying it, you could go ahead and delete it. Let me know how that goes or if you run into problems.

---

### Post by arepaking on 2009-02-01
> **caljohnsmith said:**
> I just thought I would mention that when you run gparted from the Live CD, usually you can easily unmount any mounted partition by right-clicking the partition within gparted and selecting "unmount". But to try and answer your question, your sda6 and sda9 partitions have sda7 and sda8 between them, so if you shrink sda6, you would have to move both sda7 and sda8 to the left to free up space before the sda9 partition, and then you could expand sda9 to use that space. Since you want to shrink sda6 at least 50 GB, instead of actually moving sda7 and sda8, it might be faster to copy both those partitions to the freed space you will have after shrinking sda6. Once you are done copying them there, you could mount the newly-copied sda8 partition (whatever it will be called) to make sure it is intact, and once you've confirmed that, you could delete the original sda8. And there's not much to worry about with sda7 since it is just swap, so after copying it, you could go ahead and delete it. Let me know how that goes or if you run into problems.

Thank caljohnsmith for your help. I rather err to the side of caution and I will move the freed space to sda7 then sda8 and finally allocate it into sda9. I just don't want to move the partition since I don't have so much experience in this matter. I will post my results.

Kind Regards,
AK

---

### Post by arepaking on 2009-02-01
Hi guys!
I'm glad to say that everything ran smoothly. I got all my partition sorted out. GParted is an awesome tool and it will easy any partition related task.

I attached a screen shot of my final results!

Thanks all for your support!

Regards,
AK

---

### Post by meindian523 on 2009-02-02
Glad to know everything worked out smoothly.Please mark your thread solved.

---

### Post by arepaking on 2009-02-02
> **meindian523 said:**
> Glad to know everything worked out smoothly.Please mark your thread solved.

I'll be glad to mark this post as "Solved" but I couldn't find where to do it. Where this option?

Regards,
AK

---

### Post by meindian523 on 2009-02-03
Thread Tools>>Mark as Solved,at the top of the thread,on the right above the first post.

---

### Post by arepaking on 2009-02-03
> **meindian523 said:**
> Thread Tools>>Mark as Solved,at the top of the thread,on the right above the first post.

Hi Thanks for your reply. I do not have that option when I click in Thread tools. Instead I have:

- Show Printable version
- Email this page
- Subscribe to this thread
- Add a poll to this thread

---

