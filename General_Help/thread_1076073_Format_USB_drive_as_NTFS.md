---
title: "Format USB drive as NTFS"
date: 2009-02-20
forum: General Help
---

### Post by RealG187 on 2009-02-20
In GParted 0.3.8 under the "format to" menu NTFS is dimmed out. How come it's dimmed out I need to format this hard drive as NTFS.

UPDATE: This page seems to have helped: [http://maketecheasier.com/how-to-reformat-an-external-hard-drive-to-ntfs-format-in-ubuntu-hardy/2008/09/29](http://maketecheasier.com/how-to-reformat-an-external-hard-drive-to-ntfs-format-in-ubuntu-hardy/2008/09/29)

I needed to install a the "ntfsprogs" package.

Is there a way to change (or create one since there isn't one as I just formatted) the volume labal of an NTFS drive? I think there is a command but that's for FAT, is there a GUI program?

Just as a sidenote, for command that involve identifying drives like sdac, how do **you** know which is which. I use GParted and it tells me the volume label and the sdxy identifier. Is there a better way that I don't know about?

---

### Post by Slim Odds on 2009-02-21
> **RealG187 said:**
> Just as a sidenote, for command that involve identifying drives like sdac, how do **you** know which is which. I use GParted and it tells me the volume label and the sdxy identifier. Is there a better way that I don't know about?

```
sudo fdisk -l
```
will give you a list of drives. You can find it in there.

---

### Post by RealG187 on 2009-02-21
Kinda helps you can identify drives by thier size, but I still think I like GParted better, but it's linux and there's choices and there is more than one way to do things, and users can stick to the ones they like best.

---

