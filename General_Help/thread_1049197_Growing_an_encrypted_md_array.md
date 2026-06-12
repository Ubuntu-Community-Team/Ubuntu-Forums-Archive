---
title: "Growing an encrypted md array"
date: 2009-01-24
forum: General Help
---

### Post by Kissell on 2009-01-24
I have grown a md array in the past by issuing a mdadm --grow command and then expanding the file system...

But this time its a little different...  I have encrypted /dev/md0 with luks cryptsetup.  Now I'm a little skiddish about trying to expand the encrypted array by added another disk to it.  Am I going to destroy all the data?

When I boot up the array is unusable until I unlock it with the "cryptsetup luksOpen /dev/md0 Encrypted_Data" command...  should I grow the md array before opening it?  is this okay?  will growing it mess up the encryption and cause all the data to be unreadable?  

Then after growing it, to expand the file system, I assume I would use the /dev/mapper/Encrypted_Data device and not the /dev/md0 device...  

This should work I think...  But I'm hoping to get the thumbs up from someone who knows for sure and has done it before I hit ENTER.

---

### Post by bgerlich on 2009-01-24
1.First you have resize the block device the encrypted file system is on. The encrypted file system doesn't have to be unlocked.

2. You have to unlock the encrypted volume to expand it. You have to expand the encrypted volume before expanding the filesystem.

3. In the end, you expand the filesystem.

4. Yes, to expand the file system you use the device in mapper.

Expanded encrypted RAID-0 on my home server some time ago, on debian etch or sarge, don't remember whether I've done it before or after system upgrade.

---

### Post by Kissell on 2009-02-10
I finally got up the courage to do it...  it worked flawlessly...  this is what I did...

> 
*** NOTE: ENCRYPTED FILE SYSTEM SHOULD BE UNLOCKED AND FILE SYSTEM MOUNTED/USABLE

mdadm --add /dev/md0 /dev/sdj1   (NOTE: sdj1 is the 1st partition on new drive J that will be added to the array)

mdadm --grow /dev/md0 --raid-devices=14     (NOTE: 14 is the new size of the total number of drives in array)

WAIT LIKE A DAY FOR ARRAY TO RESHAPE     (NOTE: check array status with "cat /proc/mdstat")

sudo xfs_growfs /dev/mapper/vault  (vault is the name of your unencrypted volume)


Basically the same thing for growing an array and expanding a file system volume as normal...  it being encrypted doesn't really matter or add risk, you just use the mapper device when growing the file system and not the actual device name, and if you do that then everything is like normal.

---

### Post by fjgaude on 2009-02-10
Thanks, man! It is what I would have expected but you doing it makes it real.

---

