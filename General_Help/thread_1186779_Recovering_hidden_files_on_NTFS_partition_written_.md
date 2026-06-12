---
title: "Recovering hidden files on NTFS partition written by Ubuntu"
date: 2009-06-13
forum: General Help
---

### Post by dtf21 on 2009-06-13
Hey dudes,

first posting - and I am in really big trouble. I'm totally at my wit's end and now I kindly ask you for a jump start.

Since this issue seems to be more complicated than the usual ones, a deep Google search did not make it neither. I'll try to explain:

I have two Ubuntu clients. In order to create a whole new partition table on my notebook (Ubuntu Linux 9.04), I've saved all the data of my home directory to a network share on my desktop (which is a dual boot with both Windows Vista and Ubuntu Linux 9.04). Because there was too few disk space on my desktop's Linux home directory, I've decided to share a folder on my desktop's NTFS partition.

After having re-installed the system on my notebook, I wanted to transfer back the data, that has been backed up. Now, I've forgotten to enable "Show hidden files". As you can imagine, I cut and pasted all my data from my desktop back to my notebook and it just moved all data except for the hidden directories and files (those with the preceding dot).

The status quo is: the directory was deleted by the "move" command on the desktop and the files have been gone.

Now I've tried to recover those data with a file recovery tool under Windows Vista. But this won't work, since I've had my system booted up as Linux and just had a Samba share on the NTFS partition (I assume, there's no journaling data available for Windows Vista - no clue, how this NTFS thing works).

Moment of truth: if you guys laugh about me in this very moment, I'm not angry with you, since this was a silly mistake. But now I'd really appreciate your help with this. I really need to have one hidden directory back.

Broken-hearted:
dtf21

PS: Yes, I am aware of the fact that Linux is only the kernel and not the whole system. I beg you to pardon this.

---

### Post by matthewjames on 2009-06-13
Google testdisk by CGISecurity. This runs in the terminal/cmd promp depending which o/s your on... hence yes it can run on both ubuntu and linux. Once downloaded run the file in terminal etc and do the following:

Select Create New Log File

Select the disk the old info is on

Continue till it starts scanning the drive, can take some time.

After that it will show current filesystem types. If actually found it will display the windows partition. Use your left/right arrow keys to select P, NOT *P. P is primary, *P is primary bootable. Then have grub rescan for the partition BEFORE restarting your system.

Good luck! :)

---

### Post by dtf21 on 2009-06-13
Hey Matthew,

thanks for your quick reply. I've forgotten to tell you that I've used testdisk before posting in here (I've had a little spark of hope that I don't have to tell anybody of this). I could not see any "deleted" files.

I think I'm a rookie in file recovery and so testdisk seems to be complicated. Is "my NTFS data partition is a extended logical one" an useful information at this point? You told me about "primary" partitions. I don't think that this is the case here.

At the moment I'm trying again with this scanning thing - I'll keep you posted.

Any other comments welcome.

Cheers
dtf21

---

### Post by matthewjames on 2009-06-13
Yes try switching it to "P". Then hit enter arrow over to "WRITE" and hit enter. Then if you have it, start up gparted, it should be able to see the windows partition. Good luck.

---

### Post by dtf21 on 2009-06-13
I'm not sure if I've catched your drift, but the NTFS partition is accessible without any problems.
What do you want me to do with gparted here?

---

### Post by matthewjames on 2009-06-13
> After having re-installed the system on my notebook, I wanted to transfer back the data, that has been backed up. Now, I've forgotten to enable "Show hidden files". As you can imagine, I cut and pasted all my data from my desktop back to my notebook and it just moved all data except for the hidden directories and files (those with the preceding dot).


So are you meaning that the files are still in the "Hidden Folders" on that partition or w/e? If so you can try to chmod the top level directory to all read write. Google the code for it, sorry I dont know it. Good luck.

---

### Post by dtf21 on 2009-06-13
No, the directory with the hidden files and folders in it was deleted after finishing moving the data from my desktop to my notebook *without* copying/moving (whatever) the hidden files/folders.

---

