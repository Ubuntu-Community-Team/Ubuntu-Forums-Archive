---
title: "How can I modify ISO content in Ubuntu?"
date: 2005-07-27
forum: Desktop Environments
---

### Post by unrealdark on 2005-07-27
How can I modify ISO content in Ubuntu? I mount it with forum scripts but I have Only read permission! How can I mount it writable (I need add content)?

Thnx...

 :-#

---

### Post by Shiven on 2005-07-27
run these commands:

mkdir blah
modprobe loop
mount -o loop,rw -t iso9660 /path/to/iso/file blah

that should give you read/write access to the mount... although you might have to copy it out, edit it, and then put it all back in an iso file... 

hope this helps!

---

### Post by unrealdark on 2005-07-27
[QUOTE=Shiven]run these commands:

mkdir blah
modprobe loop
mount -o loop,rw -t iso9660 /path/to/iso/file blah

that should give you read/write access to the mount... although you might have to copy it out, edit it, and then put it all back in an iso file... 

hope this helps![/QUOTE]

I have Only read permission... Yes I have to copy - modify and create new ISO...but: My old ISO has Boot info. How can I leave it in my new modified ISO?
my english!!!!  :-P

---

### Post by varunus on 2005-07-27
Can't you edit the ISO contents by using the sudo command at least?

Try mounting it somewhere in your home directory, in a folder created by the user.  You could also try changing ownership of the ISO with "sudo chown yourusername file.iso" in a terminal.

---

### Post by unrealdark on 2005-07-28
No, No write access as ROOT...  I think I have to decompress, modify and then make a new ISO.. but how can I keep boot info(original ISO)?

---

### Post by varunus on 2005-07-28
Can you post the output of "ls -l" in the directory that contains the ISO file?  Try "chmod 666 filename.iso" and then mounting it.

---

### Post by raul__ on 2006-10-29
I have the same question: how can I modify an bootable ISO image??? :-k 
I tried mount -o loop,rw ..... but I still have only read-only access! ](*,) 
Can someone help me, please? :roll:

---

