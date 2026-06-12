---
title: "Smart copying in terminal"
date: 2009-06-18
forum: General Help
---

### Post by MeLight on 2009-06-18
Hi,
I want to copy files only with certain extensions from a dir recursively to another dir, and I want to preserve the directory tree in the target directory.

Example:
the source dir is srcdir (duh):

```
srcdir/dira/
   fileg.ext1
   filef.ext2
   filed.ext3
srcdir/dirb/
   filea.ext2
   fileb.ext8
   filec.ext7

```
I only want to copy files ending with .ext2 to the target dir, which after copying will look like this:

```
trgdir/dira/
   filef.ext2
trgdir/dirb/
   filea.ext2

```
I can write a PHP script to do that, but I thought there might be a more elegant terminal solution which will also be educating for me :D.

Thanx

---

### Post by delcypher on 2009-06-18
I'm sorry I'm not very good at terminal commands but I believe you could do it by using a for loop. By cd'ing into the srcdir directory first it means the variable $filepath won't contain the srcdir/ part at the beginning so it doesn't need to be removed. I've assumed that srcdir and trgdir are in the same directory hence using ../trgdir (../ - parent directory).

```
cd srcdir/ ;for filepath in */*.ext2 ; do cp --parents $filepath ../trgdir/ ; done
```

I think this is right but don't hold me to it.

---

### Post by MeLight on 2009-06-18
Thanx for the reply.
So I will still need to write a script... I thought there was a one line terminal command solution for this kind of thing

---

### Post by Bush_Roo on 2009-06-18
Sounds like you want...

cp srcdir/dira/*.ext2 srcdir/dirb/

That's really easy... I'm not sure if that's what you want...

---

### Post by rizman on 2009-06-18
I'm still a Linux n00b, but shouldn't this work:

```

cp -r srcdir/*.ext2 trgdir

```This should recursively scan srcdir for files ending with *.ext2 and copy them to tgrdir while keeping the directory tree intact.

---

### Post by delcypher on 2009-06-18
@ rizman & Bush_Roo

Neither of those commands do what MeLight wants because MeLight wants to preserve the directory structure.

> I thought there was a one line terminal command solution for this kind of thing 

There maybe a shorter way to do it but I'm afraid I don't know it. You can put the whole thing on one line though.

```
cd srcdir/ ;for filepath in */*.ext2 ; do cp $filepath ../trgdir/$filepath; done
```

---

### Post by Bush_Roo on 2009-06-18
Oops! Yes, reclusively, that will do it!

man cp from the terminal will give you a reasonably exhaustive list of options.

Edit:

Actually... I guess I don't quite understand... I'm not sure that script does just that either...

---

### Post by rizman on 2009-06-18
> **delcypher said:**
> @ rizman & Bush_Roo

Neither of those commands do what MeLight wants because MeLight wants to preserve the directory structure.


I was under the impression that by specifying the -r option (i.e. recursively), the target directory will have the same structure as the source directory, but hey, I'm still a n00b. Also, I'm a work currently on a win pc so I can't test it right now.

---

### Post by MeLight on 2009-06-18
Thanx for the replies dudes!
It was educational after all even though there's no way of not using some kind of script here :D

---

### Post by delcypher on 2009-06-18
The recursive option won't do the job. It's okay if you want to copy everything (all folders and files) from one folder to another but if you want to be selective then you can't because the argument you give for cp on the command line is the directory you want cp to recursively copy meaning you cannot specify anything about the files in the directory.

The task would be easy if all the files were in one folder and you wanted to move everything with the .ext2 extension to a target folder. That would just be the code that rizman suggested. But MeLight has these files in multiple folders inside the source directory and MeLight wants this directory structure (the multiple folders inside the source directory) to be retained when copying the files with specific extensions.

So far only what I've suggested does what MeLight wants but there maybe a simpler way.

---

### Post by rizman on 2009-06-18
Yeah, you're right delcypher. I realised this after thinking a little bit more about it. I should really start by thinking before replying :-)

---

### Post by MeLight on 2009-06-18
I must admit I feel rather lame coz I wasn't able to run delcypher's solution (am I supposed to runn it in the terminal just like that?)
So I've written a cumbersome (30 lines!!) PHP script to do that...

A tiny explanation on the executing manner would be very appreciated

---

### Post by Bush_Roo on 2009-06-18
```
for i in $(find . -name "*.yourextension" | sed 's/^\.\///g' ) ; do cp --parents $i newdir/ ; done
```

just change 'yourextension' to the extension you of the files that you want to copy, and change 'newdir' to the destination directory.

Edit: run this in the terminal.

This script has been tested to find all the 'txt' files on my computer and reconstruct all the directories from which they came... it was quite entertaining...

It is a little rough, using 'sed' and all, but this script will work perfectly SO LONG AS YOU DON'T HAVE ANY SPACES in your filenames. I could modify it to take spaces... but... peh, didn't feel like it...

This script is more flexible than the previous one, the previous one won't go into all the little sub directories and look for files in there, but this one will.

---

### Post by delcypher on 2009-06-18
I need to think before replying as well, my code is wrong it doesn't work because the parent directories don't exist beforehand. Here's the corrected version.

```
cd srcdir/ ;for filepath in */*.ext2 ; do cp --parents $filepath ../trgdir/ ; done
```

@MeLight. Yes you just run this in the terminal. Okay an explanation then.

I've assumed that initially you start with the current working directory containing srcdir and trgdir.

1. cd srcdir/ ; - We change directory into the srcdir/ directory, this is important for the wildcard (*) to work the way we want

2. for filepath in */*.ext2 ;- This creates a for loop that cycles through values of the variable $filepath. The different values of $filepath will be everything that "*/*.ext2" matches so for example "*/*.ext2" would match "folder1/file1.ext2"  . Note ext2 is the file extension

3. do cp --parents $filepath ../trgdir/; - This is what happens during one iteration of the loop. We copy whatever $filepath is set to to the trgdir directory (seeing as it is a directory inside our parent directory we can use ../trgdir/ ). The --parents option is important because it creates any necessary directories given in $filepath in ../trgdir/

4. done; specifies to the end of for loop instructions.

Unfortunately this won't work with file names or folders with spaces in. The $filepath variable needs modifying so all spaces are escaped with the \ character. I wish I knew how to do that but I don't, sorry.

Hope that helps.

---

### Post by delcypher on 2009-06-18
Well I might of wasted my time but I've figured out how to get it to work with any spaces in the folder and file names. The code is below if anyone wants to use it.

```
cd srcdir/ ;for filepath in */*.ext2 ; do cp --parents "$filepath" ../trgdir/ ; done
```

---

### Post by Bush_Roo on 2009-07-23
Just for the record (in case someone looks this up in a Google search or something), the ULTIMATE way of doing this would be to use simply FIND and CP as follows:

```
find . -name "*.txt" -exec cp --parents '{}' ../dest/ \;
```

("../dest/" directory needs to be created before running)
(change "*.txt" to whatever extension you wish to copy)

Hope this helps someone.

---

