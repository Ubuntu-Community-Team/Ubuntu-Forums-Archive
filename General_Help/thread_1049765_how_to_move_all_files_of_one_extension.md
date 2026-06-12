---
title: "how to move all files of one extension"
date: 2009-01-24
forum: General Help
---

### Post by PierreRussellStraddler on 2009-01-24
hello

In the Documents folder on my hard drive are many many files of many different file types.

Is there a command, or set of commands, I could type into the terminal that would take all the .txt files (for example) and move them into a directory?

I know I can list them with 

ls *.txt* 

but how do I move them into a sub directory and not leave copies of them in the original Documents directory (from where they were originally collected and moved)?

thanks!:p

---

### Post by drs305 on 2009-01-24
You use the "mv" command. If they are all in the same directory:
```

mv /path.to.folder/*.txt /path.to.new.folder/

```

To learn more about this command:
```

man mv

```

---

### Post by PierreRussellStraddler on 2009-01-25
Thank you!

Here's another related question.

say there is a file called very_big_file on my internal hard drive.  I would like to move very_big_file from my internal hard drive to my external hard drive.  then I would like to erase very_big_file from my internal hard drive.

somewhere I think I read that 'mv' and 'cp' only move and copy the tiny file that points to where the large file actually resides.  said another way, how can I move the actual file itself (and not just the pointer) from the internal to the external hard drive, so when it is erased on the internal hard drive, it isn't lost?

lastly, I have many duplicate files scattered all over my hard drive.  Mostly pictures.  is there a terminal command that will search the entire file structure on a given drive for duplicate files *and* give the option to erase one of them?

as a former user of another inferior operating system, I am very much enjoying maintaining my files using the terminal.  I am also just starting to come to terms with the power linux has in terms of moving files around.  very amazing, very exciting!

once "thanks" and "solved" are enabled, I shall give you both!

thanks for your help,

Pierre Russell Straddler.

---

### Post by Egi_Power on 2009-01-26
> lastly, I have many duplicate files scattered all over my hard drive. Mostly pictures. is there a terminal command that will search the entire file structure on a given drive for duplicate files *and* give the option to erase one of them?

Unfortunately I don't know any command in the terminal for that, but I read in a magazine about some software, called FastDup that should do the job for you.
[Check out the link for it: http://dev.dereferenced.net/projects/show/fastdup]("http://dev.dereferenced.net/projects/show/fastdup")

Best regards,

Egi_Power

---

### Post by Yashiro on 2009-01-26
> somewhere I think I read that 'mv' and 'cp' only move and copy the tiny file that points to where the large file actually resides Copy always duplicates the data. There are a few gui based dupe finder tools. Track one down.

---

### Post by 3rdalbum on 2009-01-26
> **PierreRussellStraddler said:**
> 

somewhere I think I read that 'mv' and 'cp' only move and copy the tiny file that points to where the large file actually resides.  said another way, how can I move the actual file itself (and not just the pointer) from the internal to the external hard drive, so when it is erased on the internal hard drive, it isn't lost?

Like all operating systems, if you "move" a file within the same disk it will only change the pointer. If you copy a file AT ALL, or move it from one disk/partition to another, it will write a new copy.

So, copying a file from one disk to another disk will result in two full copies.

---

### Post by Egi_Power on 2009-01-26
> If you copy a file AT ALL, or move it from one disk/partition to another, it will write a new copy.

The *mv* (move) command is similar to *cp* (copy), except that rather than copying the file, the old one is removed.

---

### Post by PierreRussellStraddler on 2009-02-02
> **Egi_Power said:**
> The *mv* (move) command is similar to *cp* (copy), except that rather than copying the file, the old one is removed.


Hi everyone!

Sorry it took so long to say thank you, but I've been trying to tidy up my hardrives and get my photo situation under control!

Thanks again to everyone for all your help on this issue!

pierre russell straddler

---

### Post by SDERAWI on 2010-02-04
FsLint- For file duplicates


In nautilus   (Ctrl+s) then *.jpg or *.txt for finding the desired files with .jpg or .txt extensions

---

