---
title: "Changed SWAP partition issue"
date: 2009-04-27
forum: General Help
---

### Post by shreg on 2009-04-27
- I recently changed my swap partition to make it bigger, using gparted.

- This operation changed the UUID, but gparted still to indicate me the old UUID for the partition.

- The UUDI gaven to me by *blkin -c /dev/null* and *gparted* where the same and that is was not present in */dev/disk/by-uuid* where all the UUID should be stored.

- So I have found *vol_id -u /dev/sdaX*, wich gave me the right UUID.

- I modified the *fstab* and now my swap partition is automatically used (at least gparted tell me it is).

- This would be perfect I could use the hibernate function that was working fine before.

Now, when I hibernate it gave me no error, but when I start my computer it gave me some filesystem error and do not load the boot image of the hibernation.

I do not know if this is because it is still looking for the old swap partition at startup or something else.

I tried the following "solution" but it did not help
```
cat  /etc/initramfs-tools/conf.d/resume
That UUID should (but won't) match the UUID for SWAP in blkid so to edit:
Code:
gksudo gedit /etc/initramfs-tools/conf.d/resume
Again be sure to save > file > quit after editing! Now one last important thing:

In terminal:
Code:
sudo update-initramfs -u

```
found at [http://gparted-forum.surf4.info/viewtopic.php?id=13247](http://gparted-forum.surf4.info/viewtopic.php?id=13247)

As anyone as any idea on how to solved this issue?

Thanks

---

