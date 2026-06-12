---
title: "Make myself owner of NTFS disk?"
date: 2005-04-20
forum: Desktop Environments
---

### Post by coldturkey on 2005-04-20
I've got a 200GB HDD that i've mouned, a NTFS disc. It's running great, but i need to become the owner of it. I've tried changing the owner with nautilus but then the copyright (?) problem accured, the disc is copyrighted (?).

Could someone help me out?
Thanks in advance.

---

### Post by Alexander Kirillov on 2005-04-20
[QUOTE=coldturkey]I've got a 200GB HDD that i've mouned, a NTFS disc. It's running great, but i need to become the owner of it. I've tried changing the owner with nautilus but then the copyright (?) problem accured, the disc is copyrighted (?).

Could someone help me out?
Thanks in advance.[/QUOTE]
 It is permission, not copyright. Try running sudo nautilus

Why do you need to become owner of it? You can not write to NTFS filesystems anyway...

---

### Post by coldturkey on 2005-04-21
[QUOTE=Alexander Kirillov]It is permission, not copyright. Try running sudo nautilus

Why do you need to become owner of it? You can not write to NTFS filesystems anyway...[/QUOTE]

Thanks for telling me that >.<
What partitions can I create in Linux that can support all kinds of files, -/+ 4GB?

---

### Post by nocturn on 2005-04-21
[QUOTE=Alexander Kirillov]It is permission, not copyright. Try running sudo nautilus

Why do you need to become owner of it? You can not write to NTFS filesystems anyway...[/QUOTE]

I thought you could write, just that the Ubuntu kernel is not compiled with this (Knoppix is).
I haven't had much luck trying it though.

---

### Post by Alexander Kirillov on 2005-04-21
[QUOTE=nocturn]I thought you could write, just that the Ubuntu kernel is not compiled with this (Knoppix is).
I haven't had much luck trying it though.[/QUOTE]
 There is a kernel patch which enables NTFS write. It is considered experimental and as such, not enabled in Ubuntu kernels. But if you want the bleeding edge -- check here: 
[http://linux-ntfs.sourceforge.net/](http://linux-ntfs.sourceforge.net/)

As for the filesystems: here is an overview: [http://www.ubuntulinux.org/wiki/LinuxFilesystemsExplained/](http://www.ubuntulinux.org/wiki/LinuxFilesystemsExplained/)

---

### Post by coldturkey on 2005-04-21
Thanks all for helping out, just came from school and I've gotta watch NARUTO!
Ill try it asap!!

---

### Post by doclivingston on 2005-04-21
From what I understand it you can write to a NTFS partition, but changing the size of a file in unsupported. So I don't know if it really that useful for what you are likely to want to do with it.

Most of the things I've read have said that if you try to change the size of a file it will have a fairly large chance of destroying your NTFS partition. That could be based on old information, but it might pay to check it out thoroughly before doing something that could kill any data you have on the NTFS partition.

There are tools that can write to ext2/3 from Windows although I don't know if the tools support files > 4Gb.

---

### Post by Alexander Kirillov on 2005-04-21
[QUOTE=coldturkey]Thanks all for helping out, just came from school and I've gotta watch NARUTO!
Ill try it asap!![/QUOTE]
My advice is - do not try writing to NTSF filesystems unless there is absolutely no other way. Why not just use ext3 filesystem?

---

### Post by coldturkey on 2005-04-21
[QUOTE=Alexander Kirillov]My advice is - do not try writing to NTSF filesystems unless there is absolutely no other way. Why not just use ext3 filesystem?[/QUOTE]

I installed GParted today and Tried to convert/partition it but I couldn't do nothing.
Do I have to install anything speciell to make it work, how do I install another filesystem, ext2 or ext3?

---

### Post by Alexander Kirillov on 2005-04-21
[QUOTE=coldturkey]I installed GParted today and Tried to convert/partition it but I couldn't do nothing.
Do I have to install anything speciell to make it work, how do I install another filesystem, ext2 or ext3?[/QUOTE]
gparted is all you need. It is not very user-friendly, but there are good manuals and references - google is yourr friend. I do not remember off-hand. Did it give you any error messages? 

However, the only way to keep the files you already have there is to copy the to another HD, then reformat this one, then copy back. There is no tool (or, at least, no tool I know of) for converting files from one filesystem type to another.

---

### Post by dewey on 2005-04-21
I run a dual boot, windows2k and Hoary.  What I did, was I made a partition for my C: drive in win2k, with ntfs.  I made it big enough to hold the os, and a few games.  Then I made a fat32 partition (D: ), to hold all my music, documents, and movies.  Then I mounted it to /mnt/music with umask=000 to allow all users rw access.  It allows me to easily switch between OSs, and keep anything important.  You can't work without music. :)

As for writing to NTFS, I do not recommend it, reading is fine, but writing has a tendency to nuke your partition.  If you can, try my solution, it's fantastic.

---

### Post by doclivingston on 2005-04-21
Using fat32 works, but you can't have any files > 4Gb; although it probably isn't a problem, it doesn't support symlinks either.

One thing that is strange is that Windows won't let you create Fat32 partition greater than some certain size (32Gb? maybe), but it can use them fine if something else creates them (i.e. create it in linux, if you want to use Fat32)

---

### Post by coldturkey on 2005-04-22
[QUOTE=dewey]I run a dual boot, windows2k and Hoary.  What I did, was I made a partition for my C: drive in win2k, with ntfs.  I made it big enough to hold the os, and a few games.  Then I made a fat32 partition (D: ), to hold all my music, documents, and movies.  Then I mounted it to /mnt/music with umask=000 to allow all users rw access.  It allows me to easily switch between OSs, and keep anything important.  You can't work without music. :)

As for writing to NTFS, I do not recommend it, reading is fine, but writing has a tendency to nuke your partition.  If you can, try my solution, it's fantastic.[/QUOTE]

I've got a 20GB HDD that runs Linux atm but it's not big enough to hold the files that I need. Is there a way to make a partition on the NTFS disc (I'll probably use fat32) and move the files there, then i format the NTFS part aand remove the partition to make it whole again?

---

### Post by coldturkey on 2005-04-22
Damn.. I just made a stupid thing.. 
I unmounted my NTFS drive and ran GParted. There I converted the disc to FAT32 but I  think it also formatted it :/ Is this true or what? I don't dare to mount i :(

Yupp, everything is gone :'( Damn....

---

