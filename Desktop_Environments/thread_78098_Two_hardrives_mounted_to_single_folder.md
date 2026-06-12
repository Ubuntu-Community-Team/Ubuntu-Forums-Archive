---
title: "Two hardrives mounted to single folder"
date: 2005-10-17
forum: Desktop Environments
---

### Post by gary79 on 2005-10-17
Hi, I'm looking to sharing large amounts of video with my flatmates.

The media is stored in two hardrives but it would be nice if everyone could see both hardrives as one folder.

Question: Is it bad practice to mount multiple harddrives to a single folder?

Data protection (from hardware failure) is my concern.

Cheers,

Gary.

---

### Post by bluck on 2005-10-17
[QUOTE=gary79]Hi, I'm looking to sharing large amounts of video with my flatmates.

The media is stored in two hardrives but it would be nice if everyone could see both hardrives as one folder.

Question: Is it bad practice to mount multiple harddrives to a single folder?

Data protection (from hardware failure) is my concern.

Cheers,

Gary.[/QUOTE]

sounds to me like what you want to do is not possible without reformatting both hard drives into a RAID configuration. you cannot have two separate file systems with the same mount point. i've also heard of mounting the devices in linear mode, which would extend the one filesystem across both harddrives... you would still have to reformat one of them, and wouldnt get the redundancy you are after.

even still, if its hardware redundancy you're after, you'll lose half your available space as the option here (with 2 hard drives) is to mirror the drives.

so if all that media is almost filling both drives, you'll not be able to do this.

another option, again without redundancy, would be to soft link the files/dirs from one hdd to the other.

something like `for f in /mounted/drive1/*; do ln -s $f /mounted/drive2/;done`

---

### Post by gary79 on 2005-10-17
Symbolic links are perfect. I could just create a single shared folder and fill it full of content by symlinking to different hardrives. That way the root shared folder would remain the same no matter how many HD I have.

Cheers.

---

