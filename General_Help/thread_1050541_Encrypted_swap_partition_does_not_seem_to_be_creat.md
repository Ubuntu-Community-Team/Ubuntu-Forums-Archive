---
title: "Encrypted swap partition does not seem to be created correctly"
date: 2009-01-25
forum: General Help
---

### Post by bitbuck3t on 2009-01-25
I installed Intrepid with the alternate install cd and chose manual partitioning of my disk.  I created a swap partition as an encrypted volume with a random key.  The installer didn't indicate any errors, however while using the system, no swap seems to be available.

/etc/crypttab has
```
sda2_crypt /dev/disk/by-uuid/ /dev/urandom cipher=aes-cbc-essiv:sha256,size=256,swap
```
in it and as you can see, **/dev/disk/by-uuid/** has nothing after it.  There is also not a link in **/dev/disk/by-uuid/** for the swap partition nor one in **/dev/mapper**.

Does anyone have any suggestions or has anyone else seen this?

---

### Post by sockrebel on 2009-01-25
I was having similar problems.  Check out this thread. [http://ubuntuforums.org/showthread.php?t=848691](http://ubuntuforums.org/showthread.php?t=848691)  I used the latter part of it to fix my system.

hope that helps.

---

### Post by bitbuck3t on 2009-01-25
Thanks for the help!  After reading the post you pointed me to, I basically just did a ```
mkswap /dev/sda2
``` then got the volume_id of that partition and finally added that id to the missing field in **/etc/crypttab**.  I restarted and it seems to work!

Thanks again!

---

