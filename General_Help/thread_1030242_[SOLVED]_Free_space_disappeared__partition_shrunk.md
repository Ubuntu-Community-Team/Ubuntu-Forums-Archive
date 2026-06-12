---
title: "[SOLVED] Free space disappeared / partition shrunk"
date: 2009-01-04
forum: General Help
---

### Post by Belerophon on 2009-01-04
Hi.
I am needing some help with a partition problem 8-)

I seems that my system does not correctly sees the size of the system partition.

Recently:
[http://ubuntuforums.org/showthread.php?t=1027442](http://ubuntuforums.org/showthread.php?t=1027442)
I used partimage to save my system, delete all my partitions and make new ones where I could restore the system to. the before and after can be seen in the screenshots attached.

I all went well, and I was able to restore grub and my system was up and running again.

The problem is:

Before that operation, Gparted showed a ~29GiB system partition, using ~14GiB.
After the whole operation, Gparted shows that I have a new partition of 34GiB (that's correct, it was the size I used to create it) but there's a odd value of ~17GiB of used space. I cannot recall using 3GiB from one moment to other.
Gparted sees the correct size of the partition, but the wrong used space.

Discus, System Monitor and Disk Usage Analyser show me the correct used space but the wrong partition total size. For example, take the output of discus:
```
Mount           Total         Used         Avail      Prcnt      Graph
/               28.74 GB     11.59 GB     17.15 GB    40.3%   [****------]
+ib/init/rw      0.99 GB         0 KB      0.99 GB     0.0%   [----------]
/sys                0 KB         0 KB         0 KB     0.0%   [----------]
/var/run         0.99 GB       240 KB      0.99 GB     0.0%   [----------]
/var/lock        0.99 GB         0 KB      0.99 GB     0.0%   [----------]
/dev             0.99 GB       2.7 MB      0.99 GB     0.3%   [----------]
/dev/shm         0.99 GB       460 KB      0.99 GB     0.0%   [----------]
+onnections         0 KB         0 KB         0 KB     0.0%   [----------]
+c/volatile      0.99 GB       2.0 MB      0.99 GB     0.2%   [----------]
+media/Misc     38.76 GB     29.24 GB      9.52 GB    75.4%   [********--]
+l/security         0 KB         0 KB         0 KB     0.0%   [----------]
+infmt_misc         0 KB         0 KB         0 KB     0.0%   [----------]
+on/Private     28.74 GB     11.59 GB     17.15 GB    40.3%   [****------]
+phon/.gvfs         0 KB         0 KB         0 KB     0.0%   [----------]

```

It seems that 11.59 is the correct used space, since I cleaned up my trash. 
But 28.74 is NOT THE SIZE OF THE PARTITION I CREATED.
As discus, also system monitor and disk usage analyser show me an incorrect total size.

However, after the restore of the filesystem with partimage, through the live cd, I decided to take that chance to follow an optimization guide I found on the web:
Code:
```
sudo e2fsck -fDv /dev/sda1
```

this should optimize the directory structure and be perfectly safe...
can this be the source of the problems??

Any help would much appreciated!!

Thanks!

---

### Post by caljohnsmith on 2009-01-04
I think I might be misunderstanding, but are you saying that you restored your 29 GB partition to a 34 GB partition (via partimage), and now the new partition shows 17 GB of used space, rather than the 14 GB used space in the original partition? If that is true, how about using partimage to restore the partition to a partition of the same size, and if that works so that the used space is 14 GB like it should be, then you could use gparted to enlarge the partition to 34 GB. Would that maybe work for you?

---

### Post by Belerophon on 2009-01-04
> **caljohnsmith said:**
> I think I might be misunderstanding, but are you saying that you restored your 29 GB partition to a 34 GB partition (via partimage), and now the new partition shows 17 GB of used space, rather than the 14 GB used space in the original partition?

I am saying that I had a 29 GB partition, with 13GB of used space. This was saved using partimage, and restored again in a new partition with 34 GB of total size.

Yes, in Gparted, now I see 17GB of used space instead of the supposed 13GB. However, other tools say different things. For example, "discus" says that I have a 29GB partition...

> 
If that is true, how about using partimage to restore the partition to a partition of the same size, and if that works so that the used space is 14 GB like it should be, then you could use gparted to enlarge the partition to 34 GB. Would that maybe work for you?

Ultimately, anything will work for me as long as it gives me back the space.
But why would partimage mess with this??

But yes, that is something that I will try. Thanks for the tip, hope it works.

---

### Post by Belerophon on 2009-01-04
I have found these threads:

[http://ubuntuforums.org/archive/index.php/t-343942.html](http://ubuntuforums.org/archive/index.php/t-343942.html)
[http://ubuntuforums.org/archive/index.php/t-797305.html](http://ubuntuforums.org/archive/index.php/t-797305.html)

Tt seems that many people as problems with partimage...damn partimage:evil:

The first thread seems to be promising, and I think I will try this first and if it does not work, then try to do what was suggested by caljohnsmith.

But I will keep doing some more research first. 

Why do they, on the first thread, take off journal before resizing? resize2fs supports ext3!?...

Thanks

---

### Post by Belerophon on 2009-01-04
In fact, at:
[http://www.partimage.org/Partimage-manual_Usage](http://www.partimage.org/Partimage-manual_Usage)

> The partition to restore must have the same size as the saved partition. If the partition is smaller than the original one, the operation will fail. If it is bigger, space can be lost. You can read the FAQ of this handbook, for more details about this.

So, the fact is that they warned us....lol. Sadly, the FAQ does not help in cases that users restore a image to a bigger partition.

I should have read this first.

---

### Post by caljohnsmith on 2009-01-04
Belerophon, if you haven't all ready copied over the partition again with partimage, how about trying this to see if your new sda1 partition will recognize the correct free space:
```
sudo umount /dev/sda1
sudo e2fsck -f /dev/sda1
sudo resize2fs /dev/sda1
df -h
```
And please post the output of the above commands. Forum member meierfra has used the above technique successfully to get an ext3 partition to recognize the new larger size of the partition. How about giving it a shot and let me know what happens.

---

### Post by Belerophon on 2009-01-04
Solved. I have my 34 GB back.

Like in:
[http://ubuntuforums.org/archive/index.php/t-343942.html](http://ubuntuforums.org/archive/index.php/t-343942.html)

the problem seemed to be that I used a image belonging to a smaller partition than the one to which it was restored to. So, when that image was restored, the corresponding partition was "shrunk" (I do not know details, by far...) to the size of the original partition.

To correct it, I followed the instruction on the thread above, basically:
```

$ sudo e2fsck -f /dev/sda1
$ sudo tune2fs -O^has_journal /dev/sda1
$ sudo resize2fs /dev/sda1
$ sudo tune2fs -j /dev/sda1
$ sudo e2fsck -f /dev/sda1

```

The first filesystem check is really needed, because resize2fs asks to do it. The last is just to be sure. What I do not understand is why disable journal...? But I did not try other way... it's done.

Hope all this can help other people.

Thanks

---

### Post by Belerophon on 2009-01-04
> **caljohnsmith said:**
> Belerophon, if you haven't all ready copied over the partition again with partimage, how about trying this to see if your new sda1 partition will recognize the correct free space:
```
sudo umount /dev/sda1
sudo e2fsck -f /dev/sda1
sudo resize2fs /dev/sda1
df -h
```
And please post the output of the above commands. Forum member meierfra has used the above technique successfully to get an ext3 partition to recognize the new larger size of the partition. How about giving it a shot and let me know what happens.

I did not see your tip before my last post. Sorry.
Of course, you're right. It works like a charm. :D

I cannot post the result of the commands, as I have just done them under a live cd. I can only show what my filesystem looks like:
```
belerophon@belerophon-laptop:~ > df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              34G   12G   21G  37% /
tmpfs                1012M     0 1012M   0% /lib/init/rw
varrun               1012M  236K 1012M   1% /var/run
varlock              1012M     0 1012M   0% /var/lock
udev                 1012M  2.7M 1009M   1% /dev
tmpfs                1012M  372K 1012M   1% /dev/shm
lrm                  1012M  2.0M 1010M   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sda2              39G   30G  7.6G  80% /media/Misc
/home/belerophon/.Private
                       34G   12G   21G  37% /home/belerophon/Private
```

Thanks a lot for the help and concern!

---

