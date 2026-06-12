---
title: "Removing hard drives from the desktop view"
date: 2006-05-19
forum: Desktop Environments
---

### Post by ArrowHead83 on 2006-05-19
How can I remove the hard drives from the desktop view (while keeping them in Places -> "Computer")?

---

### Post by frodon on 2006-05-19
Go to Applications > System Tools > Configuration Editor > Apps > Nautilus and you should see some option about what appears on the desktop somewhere in there.

---

### Post by ArrowHead83 on 2006-05-19
Thank you sir! A hundred internets to you!

---

### Post by ArrowHead83 on 2006-05-19
Related question...

[list][*]How do I make it so that I can read from my NTFS drives as a user rather than root?
[*]How do I make it so that I can read/write to a FAT32 partition? (Right now I can only read from it.)[/list]

---

### Post by frodon on 2006-05-19
Your best friend is the unofficial starter guide ;) :
[http://easylinux.info/wiki/Ubuntu#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only](http://easylinux.info/wiki/Ubuntu#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only)

Feel free to post more questions, you're welcome ;)

---

### Post by ArrowHead83 on 2006-05-19
Sure. Not exactly Desktop-related, but here goes...
How do I import my Firefox bookmarks from my Windows partition, into SwiftFox in Ubuntu?
(I tried the most direct and logical course of action - importing them from SwiftFox's "Bookmarks" -> "Manage bookmarks" -> "File" -> "Import", but after choosing the bookmarks.html file, my bookmarks didn't actually show up.)

---

### Post by frodon on 2006-05-19
Strange, to be honest i would have done the same, no ideas there.

---

### Post by ArrowHead83 on 2006-05-19
Never mind... figured it out - I didn't have permissions even to read the file off of the NTFS partition as a user!........ one of the things I've been meaning to fix.

Also, when I managed to copy the file to my Home folder, the file itself still did not give me the permission to read it.

So, after a quick self-taught crash-course in the "chmod" command, I was able to change the permissions of the file and import my bookmarks. :) Problem solved.

---

