---
title: "Low disk space on filesystem root  &quot;/&quot;"
date: 2022-04-12
forum: Desktop Environments
---

### Post by cubdukat1968 on 2022-04-12
I'm having that same issue as well. I set up 20.04.3 (?) on a 250GB Samsung SSD partitioned with a 650MB /EFI partititon, a 30GB /root partition, and the rest of it /home. I wasn't even a quarter into installing all my programs when I got a nastygram that / was low on drive space. I managed to claw some back by shrinking the 18GB swap partition to 6GB since I have 32GB of RAM anyway and now I've got 7GB after deleting a couple larger programs. I'm wondering if I wouldn't just be better off redoing the installation without making a separate /root partition. I may end up doing that because of some possible errors with broken packages and unmet dependencies with build-essential and Steam.

My other choice is to shrink the /home partition by about 40GB or so, which would be my preferred method of attack because I have almost 190GB to steal from. The only problem is that gparted will only let me take the space from the end of the partition, not the beginning. Would it be possible to shrink the /home partition, then shift everything to the right until the unallocated space ends up being between the /root and swap partitions, and then I can expand /root out into that unallocated space?

---

### Post by oldfred on 2022-04-12
Thread you posted in was completed, just not posted as solved.
Moved to your own thread as solution may not be the same.

I use Kubuntu and have 30GB / partition with about 10GB used and lots of standard apps installed, but regularly housecleaned. 
What are you installing?

Post these:
sudo parted -l
df -hT -x squashfs -x tmpfs -x devtmpfs | grep -v 'snap'

---

### Post by yancek on 2022-04-13
>  Would it be possible to shrink the /home partition, 

Maybe, but we can't see your partitions so is this an msdos drive or gpt?  Post the output of fdisk -l or a gparted image of your dirve.

---

### Post by ActionParsnip on 2022-04-13
What is the output of:
```

df -h

```

---

### Post by grahammechanical on 2022-04-13
> The only problem is that gparted will only let me take the space from  the end of the partition, not the beginning. Would it be possible to  shrink the /home partition, then shift everything to the right until the  unallocated space ends up being between the /root and swap partitions,  and then I can expand /root out into that unallocated space?

Assuming that you are running GParted from a Ubuntu live session and also assuming my memory is correct, it should be possible to shrink the last partition from the left revealing unallocated space in front of the last partition that the next to last partition can be expanded into or moved across.

If that is indeed not possible then shrink the last partition from the right and then move the last partition to the right so that the unallocated space is between the last and next to last partition. Then you can expand or move across the next to last partition into the unallocated space.

GParted will let us shrink, expand, move and delete, and create partitions.

Regards

---

