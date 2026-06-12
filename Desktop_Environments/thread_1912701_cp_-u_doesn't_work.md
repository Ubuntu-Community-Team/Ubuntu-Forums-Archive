---
title: "cp -u doesn't work?"
date: 2012-01-21
forum: Desktop Environments
---

### Post by lucacerone on 2012-01-21
Hi all,
I'd like to ask you some help, because apparently I'm doing something wrong
using the -u option of cp.
I have a directory where I save my work Data.
They take a lot of space, so from time to time I want to copy them to 
an external device and remove the from my computer.

To do so I use the command
```
cp --preserve=all -R -L -v -u -t /media/externalhdd DataPath
```

I use the -u option so that only new and files that have been modified
are copied while skipping the one that I already had copied before.

Unfortunately seems that the -u option doesn't work.
If I run the same command twice in a row,
all the files are copied again.

Am I using a wrong syntax? Is there any way I can make it work
in the intended way?

Thanks a lot in advance for your help,
have a nice day!
Luca

---

### Post by ajgreeny on 2012-01-21
I can't help with that specific probem, but suggest you try using rsync rather than cp, and the command ```
rsync -r -n -t -p -v --progress /source /path/to/destination
```

I think there is a fault in the syntax, as you have no source files pathway, and perhaps ```
cp --preserve=all -R -L -v -u -t [COLOR=Red]/source/*[/COLOR] /media/externalhdd DataPath
``` I have added the source syntax into your command

---

### Post by sudodus on 2012-01-21
No I think he uses
```
       -t, --target-directory=DIRECTORY
              copy all SOURCE arguments into DIRECTORY

``` and copies from DataPath

but I agree to use rsync. It is much more powerful for backup and similar purposes.

I suggest reading
```
man rsync
```

---

### Post by lucacerone on 2012-01-21
Thanks ajgreeny, I'll try rsync.
But I think the syntax I've used is right.
Typing cp--help one of the first lines states:
> cp [OPTION]... -t DIRECTORY SOURCE....
I can't understand your suggestion to put the source before the destination directory and then write the source directory again, could you please be more clear?

Thanks a lot in any case,
cheers, 
Luca

---

### Post by sudodus on 2012-01-21
This one works for me (the u option stops overwriting as it should). I use it in Ubuntu 10.04 LTS but I am gradually switching to use rsync, which is really more powerful.

```
#! /bin/bash

echo simple backup script using cp -auv SOURCE[directory]... DESTINATION_directory
echo cp -auv $*
echo press {ENTER} to continue or {CtrlC} to quit
read
cp -auv $*

```

*Edit: Maybe it is an issue because of the file-system: If your external drive has NTFS, the file permissions will be whatever is set at mount-time for the drive. I don't know if there is also a similar problem with the time-stamps. But I think rsync can manage it (even between different computers)*

---

### Post by ajgreeny on 2012-01-21
> **sudodus said:**
> No I think he uses
```
       -t, --target-directory=DIRECTORY
              copy all SOURCE arguments into DIRECTORY

``` and copies from DataPath

but I agree to use rsync. It is much more powerful for backup and similar purposes.

I suggest reading
```
man rsync
```
Whoops!  I missed the -t option in the OP's command.

---

