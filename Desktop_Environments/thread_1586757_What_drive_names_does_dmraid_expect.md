---
title: "What drive names does dmraid expect?"
date: 2010-10-02
forum: Desktop Environments
---

### Post by cinohpa on 2010-10-02
So in general dmraid works great for discovering my my raid array and the partitions on it. I am using it right now just fine.

My problem is that on reboot, dmraid can no longer find the partitions on my raid array (there are 3 but one is the partition table). Instead it only sees the raid array.

What I do to get around this is I parted the raid array which shows up in /dev/mapper. Here I can see the partitions on my raid array and I just rename the partitions on the array. Doing this seems to make dmraid notice that the partitions exist and they suddenly show up in /dev/mapper. 

I think I broke this when I changed the names of my partitions from the names that I made the array with (which were probably some default names). 

I have tried installing and uninstalling dmraid and that doesn't work. So I wonder if there is some config file sitting around that isn't being removed or there are some partition names that dmraid is just expecting.

Thanks.

---

