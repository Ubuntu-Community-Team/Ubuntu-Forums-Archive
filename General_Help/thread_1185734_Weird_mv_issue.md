---
title: "Weird mv issue"
date: 2009-06-12
forum: General Help
---

### Post by Vrekk on 2009-06-12
OK, well the other day my desktop was covered in pictures, documents, and .iso files so I made a small shell script that would clean it up for me.  Well the line to move the .iso files was ```
mv ~/Desktop/*.iso ~/ISO\ Files
```

I ran the script and everything looked liked it worked.  But I was wrong.  The folder I wanted to move the .iso's to was "ISO files" not "ISO Files" (Case sentive :|).  Well i though it would be an easy fix, just open up "~/ISO Files" and my .iso's would be there.  I was wrong.  There isnt a folder in called ISO Files anywhere on my computer.  There is however a FILE called ISO Files thats in my home directory.  I got the idea that i could mount the file as a CD and pull the .iso's out of it, but when i mount it, it acts as if i mounted the dsl.iso that should have been in the ISO Files folder.  The problem is that i also have a windows 7 iso that should be in there.  Can someone help?

---

### Post by jenkinbr on 2009-06-12
Open a terminal and run ```
cd ~
ls -l
``` and post the output.

---

### Post by gradinaruvasile on 2009-06-12
That sucks. Now u have all ISOs in 1 file or, worse, only the last one to be moved.  It happened to me once and i lost a few hundred important files because a folder that was deleted and a script tried to move some files to it. All i was left with the last of those files. 
Did u check the file size? To see if u have them all or the last one?

---

### Post by Vrekk on 2009-06-12
drwxrwx---  13 brett brett      4096 2009-06-12 14:15 ISO files
-rwxrwx---   1 brett brett  52328448 2009-05-23 13:47 ISO Files

I just posted what was needed because the entire thing was to long.  However, I have one idea, is it possible that the mv command moved the files to my ~ and renamed it to ISO Files? If so why didn't i get an overwrite conformation when the 2nd iso was moved?

---

### Post by Vrekk on 2009-06-12
> **gradinaruvasile said:**
> 
Did u check the file size? To see if u have them all or the last one?

Last one, which is the one i dont care for anymore

---

### Post by gradinaruvasile on 2009-06-12
Exactly that happened. All the ISO s were moved to ISO Files (the file) and the last to be written remained.
Maybe its better to use mc (thats midnight commander) if u want to copy/move stuff around from the command line.
 In linux u can manipulate data in more ways than Windows and more easily... But exactly thats why u should be very careful.
I dont think you get warnings by default in command line operations. You should be extra careful here. 
And im sorry to say but that file length is about 50 megabytes... And if dsl you mentioned is DamnSmallLinux... there u have the 50 MB image...

---

### Post by Vrekk on 2009-06-12
> **gradinaruvasile said:**
> Exactly that happened. All the ISO s were moved to ISO Files (the file) and the last to be written remained.
Maybe its better to use mc (thats midnight commander) if u want to copy/move stuff around from the command line.
 In linux u can manipulate data in more ways than Windows and more easily... But exactly thats why u should be very careful.
I dont think you get warnings by default in command line operations. You should be extra careful here. 
And im sorry to say but that file length is about 50 megabytes... And if dsl you mentioned is DamnSmallLinux... there u have the 50 MB image...

Yes that DSL is DamnSmallLinux

Thanks for the help anyway, most the the iso that were erased i have on cd and i can make a new iso from the cd, but i will still have to re-download about 4-5 gigs.  This is teach me to check to make sure the command will do what I want it to do BEFORE I run it.  Well at least I fixed my Shell Script and it is working now

---

### Post by jenkinbr on 2009-06-12
I tried reproducing your situation and I get ```
mv: target `~/ISO Files' is not a directory
```

do you per chance have mv aliased to some other command?

Edit: just to mention, I always test my scripts on unimportant (dummy) files or the intended files after I back up the originals.

---

### Post by michy99 on 2009-06-12
Possibly you can recover some of the files with testdisk and photorec or ext3grep. But if you want to try you have to stop writing to that partition until you recover them.

---

### Post by Vrekk on 2009-06-12
> **jenkinbr said:**
> I tried reproducing your situation and I get ```
mv: target `~/ISO Files' is not a directory
```

do you per chance have mv aliased to some other command?


No I dont have mv aliased.  I dont know why i didnt get the error you did

When i run the command again the same thing happens, it overwrote the ISO Files with the new file

Heres what i ran

```
mv /home/brett/Desktop/test.iso ~/ISO\ Files

```

If i run it with a / at the end it works the way it should.

---

### Post by gradinaruvasile on 2009-06-12
> **jenkinbr said:**
> I tried reproducing your situation and I get ```
mv: target `~/ISO Files' is not a directory
```

do you per chance have mv aliased to some other command?

Did u put a trailing slash? If so, try without it.

---

### Post by jenkinbr on 2009-06-12
No trailing slash in my test.

---

### Post by Vrekk on 2009-06-12
Ran without it, it overwrites the file, if i add it, i get the Directory dose not exist error.

---

### Post by gradinaruvasile on 2009-06-12
There you have it. A trailing slash means explicitly directory.

---

### Post by Vrekk on 2009-06-12
> **gradinaruvasile said:**
> There you have it. A trailing slash means explicitly directory.


Then why did jenkinbr not get the same results as I did?

---

### Post by jenkinbr on 2009-06-12
> **Vrekk said:**
> Then why did jenkinbr not get the same results as I did?
my system must be a bit different?

I don't know, to be honest.

---

### Post by gradinaruvasile on 2009-06-12
Interesting
I tried moving a file named 113 in a non existing folder:

mv 113 ~/monster\ files/
mv: accessing `/home/myuser/monster files/': Not a directory

and 

mv ~/113 ~/monster\ files

The file overwrites the monster files file without question.

---

### Post by Vrekk on 2009-06-12
Hmmm I ran the code again but this time the file that i was moving was in my home directory and that time i got the error saying that ISO Files is not a Directory

EDIT: thats without the trailing slash

---

