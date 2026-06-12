---
title: "Open files staying on my computer (ex.  file.txt~)"
date: 2009-04-06
forum: Desktop Environments
---

### Post by josh6847 on 2009-04-06
I am running Ubuntu 8.04 on my laptop and when I open files, whether using vi or text editor, 90% of the time my OS leaves a copy of the file on my system.  While doing software development, I always have to go back and remove all the "opened" files.  It is really causing a huge hassle.  Is this a bug in 8.04?  I don't remember having these issues with 7.10.

Thanks,

Josh

---

### Post by mcduck on 2009-04-07
> **josh6847 said:**
> I am running Ubuntu 8.04 on my laptop and when I open files, whether using vi or text editor, 90% of the time my OS leaves a copy of the file on my system.  While doing software development, I always have to go back and remove all the "opened" files.  It is really causing a huge hassle.  Is this a bug in 8.04?  I don't remember having these issues with 7.10.

Thanks,

Josh

It's always been there, and it's not a bug. Or even anything to do with the OS.

This is a setting you can change in those program's preferences.

For example in Gedit, go to Edit/Preferences, and on the Editor-tab disable "Create a backup copy of files before saving".

---

### Post by Ratscallion on 2009-04-07
I agree with you McDuck, it has always been there, but, as far as I'm aware, they are small (usually) and hidden files, so until you enable the hidden file view, you shouldn't be able to view them. They are put in there so that if you do something wrong, and save, and want to go back, you can, just delete the new one, and remove the ~ at the end of the old one. For example, you have two files: wiggle.txt and wiggle.txt~, wiggle.txt is a huge essay (for arguments sake, I know I shouldn't use *.txt) and I accidentally delete it all, Save it, close it and reboot. However, I still have wiggle.txt~ what I do is I go back into the folder, delete wiggle.txt, and rename wiggle.txt~ to wiggle.txt. This should allow you to go back into the backup.

Again, as McDuck said, if you really want to, you can always remove the backup option.

---

### Post by rubberglove on 2009-04-07
for vim, you would want to add:

```
set nobackup
set nowritebackup
```
to your .vimrc file

---

### Post by josh6847 on 2009-04-08
alright thanks guys. that solves my problem.

---

### Post by Ratscallion on 2009-04-08
> **josh6847 said:**
> alright thanks guys. that solves my problem.
Which one(s) worked for you?

---

