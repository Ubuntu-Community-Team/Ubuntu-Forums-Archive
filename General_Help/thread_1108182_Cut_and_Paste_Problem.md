---
title: "Cut and Paste Problem"
date: 2009-03-27
forum: General Help
---

### Post by dman_dustin on 2009-03-27
I really need help. I cut and pasted a folder (with many files) to a flashdrive. Everything was fine (or so it would appear). I put the flashdrive into my laptop and I tried to do it again. But it was somehow corrupted and unreadable.

There were a lot of files in that folder, I don't know a lot about Ubuntu so I was wondering is there anything I can do to recover those files. I even predicted this was going to happen. I should have just copy and pasted but the files were eating away at my space.

So do I have to download all those files again, or is there a way I can recover those files. If it's important there was around 350 MB of files in the folder.

And I sincerely apologize if this isn't the right place, I'm just upset and sad.

---

### Post by HermanAB on 2009-03-27
Hmm, *never* use cut and paste - copy and paste yes, cut no.

The problem is that removable drives need to be mounted and unmounted carefully.  They are slooooooooow devices and what likely happened is that you yanked the device out while the copy process was still in progress.

You can try a fsck to repair the file system, but it is likely that it won't help.

---

### Post by dman_dustin on 2009-03-27
> **HermanAB said:**
> Hmm, *never* use cut and paste - copy and paste yes, cut no.

The problem is that removable drives need to be mounted and unmounted carefully.  They are slooooooooow devices and what likely happened is that you yanked the device out while the copy process was still in progress.

You can try a fsck to repair the file system, but it is likely that it won't help.

It looked like it was done. I have a Sandisk Cruzer Flashdrive that flashes when it's doing stuff and it stays glowed (orange) when it is on stanby. I waited 20 seconds or so after it stopped flashing, and then I pulled it out,

So I guess I'll have to re-download everything.

Edit: Also this is the first time this has done it.

---

### Post by jwh400 on 2009-03-27
I would ignore the blinking/not blinking of the flash drive since it may have just paused. Watch the drive's icon instead since it will change in some respect after the drive is unmounted. Your icons are likely different but watch for the change before removing the drive.

---

