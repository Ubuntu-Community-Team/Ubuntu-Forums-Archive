---
title: "Pulling netatalk data from a Mandrake server, before &quot;Ubunting&quot; it!"
date: 2006-02-01
forum: Desktop Environments
---

### Post by AlexMorin on 2006-02-01
Hello all! (If I'm in the wrong forum, feel free to correct me.)

I'm working on pulling data off an old non-functionnal Mandrake server in order to install Edubuntu on it. This server will not boot properly off it's hard drive (the filesystem is read-only on / and it keeps throwing up segmentation faults). Long story short : there is data on there that I need, and it was put there by Mac computers using Netatalk. And I am in Montreal, so accented (éèàù) characters are in the names of files and folders.

I'm trying my luck withn Knoppix. I also have Breezy and Dappper (daily) LiveCDs, but haven't really tried them.
Now, using Knoppix, I can mount the drives rw and transfer files using a USB drive or SMB to my Mac.

Problem: the accented characters are gone from the file names. So whenever it try to copy a folder, I get errors:
Using cp -R :
"cp:  cannot create regular file '/pathToDestination/m:8el':  Invalid argument" 
That file should be named "mél", not "m:8el"
Using the GUI :
"Could not make folder /pathToDestination/C:83"

 I have tried some commands and scripts to replace the ":83" and its friends to "eee" or "___", but nothing that does it recursively. We are talking about lots of data (2 gigs).
I've also tried ta archive the folders to .tar.gz with some success. But some of the archives will not decompress properly, probably because of the filenames, and the console.log on my Mac is complaining about timestamps on these file being in the future...
I have tried to remount the filesystem with iocharset=utf8, but that option is not valid. It's an ext3 drive. There is also an ext2 drive in the system. Both have the data I want. The original location of the data is on the ext2 drive.

Question: what do I do next? Is there a way to get the proper file names back? How can I get this data off this server so I can finally make it live the Ubuntu life?

---

### Post by AlexMorin on 2006-02-03
Anyone? Did I forget important details that would help you guys help me? This school is really in deep without this data...

I'm really stuck here. And I am not a Linux specialist. But I enjoy it quite a bit!

---

### Post by AlexMorin on 2006-02-08
I tried a Mandriva LiveCD but it won't boot completely. It stays at the bleu penguin screen.

I'm trying a Gentoo RescueCD to SSH (scp) the files to my laptop.

---

### Post by AlexMorin on 2006-02-08
FIXED!

I had success using scp to copy the data.

Thanks!

---

