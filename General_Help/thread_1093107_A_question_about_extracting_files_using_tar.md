---
title: "A question about extracting files using tar"
date: 2009-03-11
forum: General Help
---

### Post by Azdour on 2009-03-11
Hi All,

If I'm using tar to extract files and the tar hits a permissions issue extracting a file, does the the tar stop extracting or does it just skip the problem files? I'm hoping it's the latter.

---

### Post by hyper_ch on 2009-03-11
can you post the error?

---

### Post by Azdour on 2009-03-11
The error I get is:

tar: home/someuser/.gvfs: Cannot utime: Permission denied
tar: home/someuser/.gvfs: Cannot change ownership to uid 1000, gid 1000: Permission denied
tar: home/someuser/.gvfs: Cannot change mode to rwx------: Permission denied
tar: Error exit delayed from previous errors

I think this actually occurs at the end of the extract when tar attempts to put the permissions, groups and user onto the extracted files. I'm currently logged in as someuser so some of the home files are probably in use.

I just wanted to know overall how tar handles problems with files/directories, and does it proceed extracting the other files? I'd hate to do a restore and find that because of an issue with a file it only partially extracted :)

---

### Post by 3Miro on 2009-03-11
You can try and ue a graphical manager to extract specific files from the tar file. Other than that, I don't know ho errors are handled.

---

### Post by whitethorn on 2009-03-11
Where are you taring to? As in how is the partition formatted? fat32/ext3, fat32 doesn't keep file permissions.  What command are you using, there are some options with tar to keep the permissions intact.

---

