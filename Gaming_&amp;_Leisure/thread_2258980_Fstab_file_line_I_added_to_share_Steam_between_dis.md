---
title: "Fstab file line I added to share Steam between distros makes NTFS partition invisible"
date: 2015-01-01
forum: Gaming &amp; Leisure
---

### Post by Cleaver on 2015-01-01
Hi!

I have followed the instructions here using Ubuntu to put my main Steam games folder on a NTFS partition I use for data(which I label "DATA" and will refer to as that or "data partition" from now on:  [https://support.steampowered.com/kb_article.php?ref=7611-FHLZ-4319](https://support.steampowered.com/kb_article.php?ref=7611-FHLZ-4319)

I'm a multibooter for various reasons, so this data partition is the best place for me to put things that large. The instructions themselves seem to work as far as allowing me to install games to that folder, but the file manager doesn't show the data partition in the left panel once I've edited the fstab file and rebooted. This prevents a huge problem, as it currently seems as though I can either use this folder for Steam OR be able to manage that partition in Linux, but not both.

Any suggestions? Thanks in advance!

---

### Post by deadflowr on 2015-01-01
What is the mount point you used, example /home/user/Somenewfolderyoumade/?
Because that is now where the system will show it.
When you add mount points to the fstab they are no longer considered external.
So they will no longer be listed in the left panel's devices section.

If you want to have the partition show in the panel, then bookmark the folder/directory that it is connected to.

---

### Post by Cleaver on 2015-01-02
The folder is listed in Steam as: /data/Steam[Linux]

Is that what you mean by mount point? I have only a partial understanding of mounting, but what you just said might be pointing me onto the right track.

However, I just looked under "computer" which I'm starting to think must be simply listed as "/" outside of the file manager, and saw my "data" folder that represents the partition I'm looking for. Does that mean all I have to do is look there to manage files like normal, and that the only difference is that it won't show up in the left panel?

Thanks again for your reply!

---

### Post by deadflowr on 2015-01-03
Basically whatever you put as the mountpoint in the fstab file is where the partition is going to appear in the system.
I'm guessing you made a folder called /data, and that /data is in the fstab entry for the partition.

The reason it no longer appears on the left side pane is because it is now an internal part of the overall system.
Where as before Ubuntu treated it as an external entity.
Which if you noticed is why in the left pane it was listed under a section called Devices.

But a quick solution, if you will, would be to drag and drop the folder to the left side pane's bookmark area.
Then you'll see it there for quick access if you want.

If any of this makes sense.

---

