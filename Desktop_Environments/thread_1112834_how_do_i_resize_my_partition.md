---
title: "how do i resize my partition?"
date: 2009-04-01
forum: Desktop Environments
---

### Post by shamimkhaliq on 2009-04-01
i need to resize the current system to free up enough space and create the new partition from a liveCD like gparted to ensure no issues with mounted filesystems. i don't suppose you could do me the hugest favour and walk me through it? like install live cd>get apt ?>applications>?>select ? it's just i've looked at partitioning programs and they make little sense to me.

---

### Post by immy123 on 2009-04-01
You can resize your partition using Gparted. But, you should log into Ubuntu using a live CD. Open gparted and right-click on the partition you want to resize. Then hit Resize/Move. Then under new size, change to the size you want your partition to be. You can only decrease the partition in this case. But, if you want to increase it size, then you have to choose another partition and decrease its size, so that that space will be free to be added to your new partition.

---

### Post by adamlau on 2009-04-01
I am assuming that you are not using XFS. If so, I prefer to boot up Gparted Live over the Ubuntu ISO.

---

