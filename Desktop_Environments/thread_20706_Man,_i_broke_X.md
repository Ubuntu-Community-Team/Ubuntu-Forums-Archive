---
title: "Man, i broke X"
date: 2005-03-18
forum: Desktop Environments
---

### Post by Slapdash on 2005-03-18
how does one rename a file in terminal to the UKNOWN extension backup file?
I have the file X86Conf-4 and  X86Conf-4~  when I LS.

how do i get the last one to look like the first one?
I edited my X86 conf file and now I cant boot into X   :oops:

---

### Post by bored2k on 2005-03-18
[QUOTE=Slapdash]how does one rename a file in terminal to the UKNOWN extension backup file?
I have the file X86Conf-4 and  X86Conf-4~  when I LS.

how do i get the last one to look like the first one?
I edited my X86 conf file and now I cant boot into X   :oops:[/QUOTE]
 I didn't understand.

Here is what I understand:
You edited, made crap out of it and now want to recover the other one right ?

Well
ls -a /etc/X11/ will show you hidden files

Depending on the editor the filename of the backup will also.
If you used nano will probably be filename.list_backup
If you used joe filename.list~
Gedit no freaking idea.

How do you rename in Shell ?
mv filename.list.backup filename.list

---

### Post by Slapdash on 2005-03-18
Ah you understand right-  Thanks i'll got try Patch it tonight. lol
I think it was nano yeah, the default editor?

---

