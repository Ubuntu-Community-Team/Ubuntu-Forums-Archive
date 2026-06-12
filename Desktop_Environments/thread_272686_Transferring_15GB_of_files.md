---
title: "Transferring 15GB of files"
date: 2006-10-06
forum: Desktop Environments
---

### Post by Jordan Meeter on 2006-10-06
Hey all,

I have Ubuntu/Windows dual booted on my computer. I have a 'My Music' folder on Windows with 15GB of music in it. Is there any way I can transfer these files "internally"? I have heard things about people mounting Windows and being able to access their files.

Is there any way to do this, without burning 22 CDs?

Thanks,
Jordan

---

### Post by Omnios on 2006-10-06
This is the wiki on mounting win files.

[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

also see

[https://wiki.ubuntu.com/FindPage?action=fullsearch&titlesearch=1&value=mount\]("https://wiki.ubuntu.com/FindPage?action=fullsearch&titlesearch=1&value=mount")

 Also I dual boot so I whent to a more pernament solution by using QTparted to make a Vfat 32 My documents partition that works like My Documents in  XP and as a documents drive in Linux. This has proven to be very usefull over the years.

---

### Post by Jordan Meeter on 2006-10-06
So will I then be able to 'drag and drop' the files from Windows to Ubuntu?

---

### Post by Omnios on 2006-10-06
> **Jordan Meeter said:**
> So will I then be able to 'drag and drop' the files from Windows to Ubuntu?

 You will not be able to cut or write to ntfs but will be able to copy them to your Ubuntu partition.

---

### Post by Jordan Meeter on 2006-10-06
Should I do this via terminal?

---

### Post by Omnios on 2006-10-06
> **Jordan Meeter said:**
> Should I do this via terminal?

Mounting as in the wiki should be done by the terminal.

---

### Post by Jordan Meeter on 2006-10-06
I mean transferring the files...

---

### Post by Omnios on 2006-10-06
> **Jordan Meeter said:**
> I mean transferring the files...

Counting on how you mounted the drive you should be able to drag and drop.

---

