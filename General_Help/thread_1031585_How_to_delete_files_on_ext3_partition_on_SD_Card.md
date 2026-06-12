---
title: "How to delete files on ext3 partition on SD Card"
date: 2009-01-05
forum: General Help
---

### Post by hurdy on 2009-01-05
Hi everyone,

Firstly thank you for taking the time to read this.

I want to delete files from 1 of 2 partitions on an SD card. My SD Card has 2 partitions, one is an MsDOS and the second ext3 partition.

With the MsDos Partition I was able to just delete the files via the ubuntu GUI. This cannot be done for the ext3 partition where it flags the errors     "The folder "folder_name" cannot be handled because you do not have permissions to read it."

I have mounted the SD card partitions with no trouble. The partition in question is mounted at location "/mnt/sdf4".

Any advice how I can delete the files would be great. I am a newbie to the linux way of things.

Many thanks,

Rob

---

### Post by SteveDee on 2009-01-05
You need to run nautilus from a terminal using; sudo nautilus.
 
You can then select the folder, right click and select Properties > Permissions and make yourself the owner. Also click on "Apply Permissions to enclosed files"

Close Nautilus, then just re-open it via "Places". You should now be able to delete files in that folder.

---

### Post by ezsit on 2009-01-05
Easy Method:

From the command line (terminal) with sudo:

sudo rm -r /mnt/sdf4/name_of_folder

This will delete the entire folder and all contents. Of you can cd into the folder and:

sudo rm filename

Sudo will ask for your password and then do the rm (remove) command with root privileges, bypassing the permissions and ownership issues.

---

### Post by hurdy on 2009-01-05
excellent. Thank you very much guys!

I appreciate your assistance.

Rob

---

