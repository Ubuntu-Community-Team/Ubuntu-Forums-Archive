---
title: "Help with understanding the ubuntu customization process"
date: 2009-03-08
forum: Development CD/DVD Image Testing
---

### Post by JeyPeyy on 2009-03-08
I'm doing this project at school where I should do my own custom Linux-distro. I chose to customize Ubuntu to do this. Here's the website: [http://winuxos.tk/](http://winuxos.tk/) (lol @ dot.tk, I know, but I haven't had the time setting up a server yet :P). I've mostly worked with [this]("https://help.ubuntu.com/community/LiveCDCustomization").

So now I have to write what I have learnt, but I don't understand everything. Especially not the "Putting the CD together"-part. So, here's some questions:

[LIST]
[*]Is filesystem.manifest really needed? Won't the installer copy everything from filesystem.squashfs? 
[*]What is that 'sed' thingy? I can't find anything about '-i' in the man page
[*]How do md5sum work?
[/LIST]

---

### Post by Sorivenul on 2009-03-08
> **JeyPeyy said:**
> [LIST]
[*]Is filesystem.manifest really needed? Won't the installer copy everything from filesystem.squashfs? 
[*]What is that 'sed' thingy? I can't find anything about '-i' in the man page
[*]How do md5sum work?
[/LIST]
filesystem.manifest, to my knowledge, contains the files installed within the squashfs, and the filesystem.manifest-desktop contains packages that will be installed during installation.

sed is a "stream editor". It is popularly used to do search-and-replace for specific text in a file. "-i" means "in-place", and edits the specified file in place, making a backup as necessary. The syntax would be like:
```
sed -i[SUFFIX] filename
```
[SUFFIX] would be what would be appended to a backup copy of the file, AFAIK.

md5sums are, in reality, a pretty advanced topic dealing with algorithms. We make light use of them for checking file integrity. Basically, the md5sum command hashes the information passed to it (in the case of a LiveCD, it is an ISO image), and returns a corresponding checksum. On the user end, they can likewise perform an md5sum, to compare to the original, to make sure the file hasn't been tampered with or corrupted.

---

