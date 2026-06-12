---
title: "Can I recover a partition that has not been fully formatted?"
date: 2011-02-06
forum: Desktop Environments
---

### Post by bisharkha on 2011-02-06
Hi,
A while ago I accidentally started an Ubuntu Server 10 installation over  my data drive. The drive was ext4 formatted and only contained data (no  OS and only 1 partition).
However when the installer kicked the partition editor into action  (after I selected "use entire disk" option (basically letting the  installer decide the partitioning)). When I noticed that the  partitioning was taking a little longer than I expected (no other  processes had begun) I powered down my machine before any other disk  access could happen.
Now I have a server type partition scheme on the disk with no data because I never let the writing of files to begin.
I have used everything from gpart, foremost, testdisk, photorec, etc. I  had a lot of data and now I can only pull up the files that will take  forever to sort (if at all). Besides one run on testdisk on the actual  disk I have run all the other tests on a dd image.
I was wondering if there is a way to get my old partition back since I  never wrote any data to it (unless my understanding of the install  process is wrong). When I pull the disk up in gparted I see that it  reports the disk as having data (the GB value of which matches my  recollection of how much of the disk I had used). I tried to see if any  backup superblocks might be able to help but they all show up as blank.  Now I see a yellow block in gparted that seems to indicate that it  somehow can detect that there is data there but it shows no accessible  partitions.
I don't want to know how to recover the data (the tests I performed  returned a good number of files that I feel I can recover files if I  wanted).
I was wondering if anybody might be able to show me how to  recover/restore the original partition structure so I would not have to  recover the data - the file structure would just be returned to the way  it was. I tried to reformat a dd image with as close to the original as I  could but that did not do anything.
I know this is long but it's worth asking when you lose all your kids'  pictures and videos and all the data and info I had gathered starting  almost 12-15 years ago.

---

