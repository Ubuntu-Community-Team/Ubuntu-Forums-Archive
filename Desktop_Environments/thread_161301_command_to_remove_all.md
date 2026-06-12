---
title: "command to remove all?"
date: 2006-04-16
forum: Desktop Environments
---

### Post by zorlab on 2006-04-16
as root I have downloaded and extracted alot of files, directories with many full sub-dirs

How can I remove all of this, without painstakingly picking each file and dir?

In the filesystem I get permission denighed.
 I have tried rmdir --help
man
man remove directoried, 
apropos remove directories,    etc.. 

Seach hear found me no info  here,  and google didnt help

can someone  help please??](*,)

---

### Post by ubernoob on 2006-04-16
-r is recursive
so you can do "rm -r folder"

but be carefull when you do this. All subfolders and files will be deleted

---

### Post by applechewer_ on 2006-04-16
use "sudo rm -R <directoryname>"

that should remove the directory, and the contents of all subdirectories

---

### Post by 5-HT on 2006-04-16
i) To remove files and directories recursively with root privileges, and have an interactive prompt asking you confirmation for each removal: ```
 rm -ri <path to directory> 
``` 
e.g., say you have a directory /opt/foo with may subdirectories and files within it.
```
sudo rm -ri /opt/foo 
``` 
ii) To remove files and directories recursively with root priviledges without having an interactive prompt asking confirmation for each removal* **: ```
sudo rm -rf <path to directory>

OR

sudo rm -r <path to directory>
``` 

* Be VERY careful with this one, if you make a mistake, you could end up wiping out the whole drive
** The default behaviour of 'rm -r' is to delete everything without confirmation (i.e., it assumes the 'f' flag).

e.g., say you have a directory /opt/foo with many subdirectores and files within it

```
sudo rm -rf /opt/foo

OR

sudo rm -r /opt/foo 
``` 

iii) To read more about the rm command:
```
 man rm 
```

---

### Post by zorlab on 2006-04-16
Thanks all!  so much info,  I am saving this page! :-D

---

