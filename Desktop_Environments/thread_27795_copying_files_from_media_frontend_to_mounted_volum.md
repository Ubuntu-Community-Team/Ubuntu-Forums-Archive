---
title: "copying files from media:/ frontend to mounted volume takes too long"
date: 2005-04-17
forum: Desktop Environments
---

### Post by tharsan on 2005-04-17
If I open up the 'Storage Media' shortcut from the System Places, and open a mounted partition (for this example, I use hda2).
I try to copy a file from the right-side of Konquerer, to the left (where the Media tree is shown), but in the same partition.  The file attempts to copy, but it takes a while (although it should be instantaneous as I'm working in the same partition).

I believe it is because the source is file:///mnt/hda2/file and the destination is media:/hda2/Folder/file.

If I enter 'cp /mnt/hda2/file /mnt/hda2/Folder/', then the transfer is instantaneous (as expected).

There should be some way to make Konquerer use media:/.. for both source & destination, or use /mnt/... for both source & destination.

Thanks
- Tharsan

---

