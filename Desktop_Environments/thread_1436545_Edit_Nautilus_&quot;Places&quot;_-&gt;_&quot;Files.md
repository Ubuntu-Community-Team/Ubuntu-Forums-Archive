---
title: "Edit Nautilus &quot;Places&quot; -&gt; &quot;Filesystem&quot; entries"
date: 2010-03-22
forum: Desktop Environments
---

### Post by bdlang on 2010-03-22
Is there a way to edit or remove the Nautilus "Places" -> "Filesystem" entries? Just below the "Computer" entry I've got too many filesystem entries that I'd like to remove. I just want the "Computer" entry, I don't need to see all the other filesystems on the HDD that I don't mount on a regular basis (they appear to be FreeBSD slice entries anyway).

---

### Post by agjino on 2011-03-26
This is an old thread, but since it shows up in Google search I'll post an answer.

This has worked for me on Ubuntu 10.10 Maverick Meerkat:

1. Find the mount point of the filesystem you want to hide through:

albi@SPARTA:~$ sudo blkid
**/dev/sda1**: LABEL="System Reserved" UUID="AA2201DF2201B0FD" TYPE="ntfs" 
/dev/sda2: LABEL="Win7" UUID="8E6C07BB6C079D59" TYPE="ntfs" 
/dev/sda5: UUID="89954b07-0b5a-4159-a2bc-60656ed8f7ea" TYPE="ext4" 
/dev/sda6: UUID="7f5802fa-934e-4b07-b6e7-86f55be1e0f7" TYPE="swap" 
albi@SPARTA:~$ 

Say, I want to hide **/dev/sda1** (a 100MB filesystem created by the Windows 7 install).

2. Create a file in /etc/udev/rules.d/:

albi@SPARTA:~$ sudo gedit /etc/udev/rules.d/10-hide-partitions.rules

3. Paste the following text in the newly created file and save:

ACTION!="add|change", GOTO="hide_partition_end"
SUBSYSTEM!="block", GOTO="hide_partition_end"
KERNEL=="loop*|ram*", GOTO="hide_partition_end"
KERNEL=="**sda1**", ENV{UDISKS_PRESENTATION_HIDE}="1"
LABEL="hide_partition_end"

4. On reboot /dev/sda1 aka. "System Reserved" should not show up in Gnome Places.

Solution taken from: [http://askubuntu.com/questions/16904/how-do-i-hide-cifs-volumes-in-the-places-menu](http://askubuntu.com/questions/16904/how-do-i-hide-cifs-volumes-in-the-places-menu)

---

