---
title: "Extracting and uncompressing files from tarball"
date: 2009-05-22
forum: General Help
---

### Post by pseudo_nz on 2009-05-22
I backed up my home directory using kbackup, which compressed everything into a tarball.  Now I want to restore random files, rather than the entire thing, but when I extract the top folder using Ark or Archive Manager, everything inside it is still compressed as bz2 files.

I know I can extract each one manually, but I have about 5000 image files I want to restore, and don't really want to have to that by hand, so is there a command or an application that will do it for me?  I would want to be able to control where they are being extracted to, and have each subfolder automatically done as well.

Thanks for any advice...

---

### Post by KhurramM on 2009-05-22
untar first the main file using:

tar -xjf whatever.tar.bz2 -C /destination-folder

goto /destination-folder

next when all files show:

tar -xjf *.tar.bz2

For other options:
man tar

---

### Post by pseudo_nz on 2009-05-22
Thanks for the response.

The file that the backup program gave me was just .tar, not compressed, so I've got as far as extracting everything into a folder on my desktop.  I think all I need to crack is the right commands to get bunzip to decompress everything inside a specific folder, including stuff in subfolders, but so far no luck.  Am learning all sorts of random, almost-related stuff from Google tho, lol.

---

### Post by unutbu on 2009-05-22
pseudo_nz, I'm not sure I understand your situation. Do you have a directory that is full of .bz2 files? If you'd like to bunzip all of them, you could run
```

find /path/to/top/level/dir -name "*.bz2" -exec bunzip2 {} \;
```

Any backup program worthy of the name should also come with an easy method to restore files from backup. If your current backup strategy does not provide this, I'd humbly suggest looking for another backup program.

---

### Post by pseudo_nz on 2009-05-23
> **unutbu said:**
> Any backup program worthy of the name should also come with an easy method to restore files from backup. If your current backup strategy does not provide this, I'd humbly suggest looking for another backup program.

Thank you so much for that, it worked perfectly! :KS

The backup program I used was the first one I saw; I just wanted to slap everything onto removable media before installing Fedora.  A day later, I was back on Ubuntu, this time with the proper home partition setup, but I didn't want to restore all my previous settings, I just want to pick and choose which files to put back on the hard drive.

As for a backup system, I'm looking at getting an EHD big enough that I won't have to worry about compression.

---

