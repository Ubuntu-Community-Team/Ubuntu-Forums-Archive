---
title: "If I set Ubuntu on FAT32 as apposed to the Linux file format what happens?"
date: 2005-12-12
forum: General Help
---

### Post by eXSBass on 2005-12-12
I want to be able to access my Windows files from Ubuntu and vice versa. I'm currently on I think Ext3fs and am going to reformat. Before I do and decide to change to FAT32, is there anything I should know?

Reduced performance? Side effects? Anything?

---

### Post by psusi on 2005-12-12
You can not install linux on a fat32 partition because it does not store posix file attributes ( file owner, permissions, etc ).  You can set aside a fat32 partition for shared files, but you need to install ubuntu on a unix like filesystem.  

You also don't have to reformat to do this.  Assuming you have free space on an existing partition, you can shrink one down to free up some space, and turn that space into a new fat32 partition to share data on.  Boot up on the ubuntu livecd and fire up gparted.  

[QUOTE=eXSBass]I want to be able to access my Windows files from Ubuntu and vice versa. I'm currently on I think Ext3fs and am going to reformat. Before I do and decide to change to FAT32, is there anything I should know?

Reduced performance? Side effects? Anything?[/QUOTE]

---

### Post by DrBair on 2005-12-12
You also have the option of getting an ext2/3 viewer for windows.  

But like he said, we need a file system with POSIX attributes. FAT32 won't cut it.

---

