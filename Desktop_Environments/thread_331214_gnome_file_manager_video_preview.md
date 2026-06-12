---
title: "gnome file manager video preview"
date: 2007-01-04
forum: Desktop Environments
---

### Post by chris_andrew on 2007-01-04
Hi,

I have just done a fresh install of Etchy.  On my last install, some of my video files (mpeg's) were previewed in the (nautilus) file manager.

What I mean is that as the file emblem, it would show a freeze frame of the video.

Well this doesn't happen, now.  Anyone know how I can turn it on?

Many thanks,

Chris.

---

### Post by 23meg on 2007-01-04
In the file management preferences, go to the "Preview" tab and make sure the appropriate option is selected.

---

### Post by chris_andrew on 2007-01-04
Did that, still no difference.  I selected that it should be done for all files, below 1gb.  No change :-(.

---

### Post by meng on 2007-01-04
I assume these are local files, not on a network drive.

---

### Post by chris_andrew on 2007-01-04
Yup, on my local /home partition.

---

### Post by 23meg on 2007-01-04
Does this happen to all files? If it happens to some files only, try moving those files to another folder, and then back to their original folder and refreshing the Nautilus view (F5).

---

### Post by chris_andrew on 2007-01-04
Hmm, just tried your suggestion.

The preview doesn't work in any part of my /home.

Thanks,

Chris.

---

### Post by rastakun on 2007-02-12
Try this, go to your folder with the video files and
$touch *.mpg
(if .mpg is your file ending, otherwise change it to what the files have) and then refresh.

Hope it helps.

/rasta

---

### Post by tgoose on 2007-03-11
I'm getting what I can only assume is the same problem as this. No files in / will preview (and dirs show with "--" instead of the number of items inside.) This happened after messing around removing partitions of other OSes, but files everywhere else preview fine. I've moved files from one location to another and "touch"ed them, but still nothing. Any ideas? Thanks.

edit: this changes if I set previewing to work on all files, instead of just local ones. Which is an OK fix, but not if I want to browse any network shares etc... How can I tell it that / is a local drive?

second edit: Never mind, I've worked it out myself. For some reason the entries for a whole load of partitions became commented out in /etc/fstab . I uncommented them and it's all fine.

---

