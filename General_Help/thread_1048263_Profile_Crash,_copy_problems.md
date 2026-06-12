---
title: "Profile Crash, copy problems"
date: 2009-01-23
forum: General Help
---

### Post by GMarkow on 2009-01-23
Hi all,
   I'm running Hardy and recently my primary profile crashed. Something to do with Nautilus not shuting down properly. I plan on fixing the issue by doing a fresh install/upgrade. 

My problem is that I can't copy my home folder. I have tried copying the folder onto an external hard drive, whcih normally would work but now I don't have permission to read/write to the drive. 

I've also tried to copy the home folder to another profile on my system using    

sudo cp /home /greg /home/guest1

greg being the directory to be copied

The terminal spits back 
"omitting greg"

So now I'm stuck. Does anyone know how I can copy my home folder?
Best
Greg

---

### Post by sisco311 on 2009-01-23
```
sudo cp -r /home /greg /home/guest1
```

> My problem is that I can't copy my home folder. I have tried copying the folder onto an external hard drive, whcih normally would work but now I don't have permission to read/write to the drive.

post:
```
sudo fdisk -l
```and
```
mount
```

---

### Post by GMarkow on 2009-01-23
Thanks a ton Sisco. 

I'm a fairly new user so I'm still trying to learn. I ran, cp --help and saw that -r meant to do things recursivly. But I don't really understand what that means. Would you mind explaining what the -r argument did and why the directory to be copied was 'omitted' with out -r ?
Thank you
Greg

---

### Post by sisco311 on 2009-01-24
cp = copy a single file
cp -r = copy a directory, its subdirectories and the files it holds


[Recursion]("http://en.wikipedia.org/wiki/Recursion"), in mathematics and computer science, is a method of defining functions in which the function being defined is applied within its own definition. The term is also used more generally to describe a process of repeating objects in a self-similar way. For instance, when the surfaces of two mirrors are almost parallel with each other the nested images that occur are a form of recursion.

In Linux and Unix, everything is a file. Directories are files, files are files and devices are files. Devices are usually referred to as a node; however, they are still files. 

The cp command without the -r option (flag) only knows how to copy a single file if the file is not a directory.

The recursive definition of the cp command is something like:
[list=1]
[*]if no files left, then you are done.
[*]cp the file and if the file is a directory cp the files it holds.
[/list]

e.g.

foo
foo/1.txt
foo/2.txt
foo/bar/3.txt
foo/bar/4.txt

cp -r foo new

[list=1]
[*]cp foo new, foo is a directory => cp the files it holds:
[list=a]
[*]cp 1.txt new/1.txt, 1.txt is a file => done
[*]cp 2.txt new/2.txt, 2.txt is a file => done
[*]cp bar new/bar, bar is a directory => cp the files it holds:
[list=i]
[*]cp 3.txt new/bar/3.txt, 3.txt is a file => done
[*]cp 4.txt new/bar/4.txt, 4.txt is a file => done
[/list]
[/list]
[*]no files left => done
[/list]

---

