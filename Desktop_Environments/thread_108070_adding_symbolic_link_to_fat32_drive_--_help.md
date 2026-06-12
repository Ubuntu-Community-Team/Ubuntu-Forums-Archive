---
title: "adding symbolic link to fat32 drive -- help"
date: 2005-12-24
forum: Desktop Environments
---

### Post by linuxNewb on 2005-12-24
I have a dual-boot windowsxp/ubuntu breezy. I made a fat32 data partition that both can access. I have my root apache2 folder on the fat32 drive. I want to make a symbolic link to my mp3 folder so I can stream mp3s to my windowsxp entertainment center. The problem is that when I try to make a symbolic link on the fat32 drive, I keep getting 'action not permitted'. I even tried it as root. 

How can I make a symbolic link on a fat32 data drive?

---

### Post by sciurus on 2005-12-25
You can't. The fat32 filesystem (or ntfs, for that matter) doesn't support symbolic links.

---

### Post by zoiks on 2005-12-25
I think doing apache on a fat partition is really a bad idea.  Not only does it not support many important things (like symlinks) it also won't properly handle file permissions.  Bad idea for a web server!

---

