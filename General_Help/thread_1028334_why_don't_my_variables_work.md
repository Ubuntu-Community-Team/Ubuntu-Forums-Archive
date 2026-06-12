---
title: "why don't my variables work?"
date: 2009-01-02
forum: General Help
---

### Post by sn0m on 2009-01-02
I'm trying to write a script so I can back up important files periodically using cron.

this is it:

#!/bin/bash
#script to back up documents
#Variables
DATE=$(date +%d-%B-%Y)
FILE1=$/home/sn0m/back_up
FILE2=$/home/sn0m/disk1/backup_prova
------------------------------------------------------------------------------

/bin/mount -t ntfs /dev/sda4 /home/sn0m/disk1

----------------------------------------------------------------------------

cd /home/sn0m

------------------------------------------------------------------------------
#copy experimental folder

/usr/bin/rsync -avz $FILE1/ /home/sn0m/disk1/$FILE2.$DATE

----------------------------------------------------------------------------
#unmount backup drive

/bin/umount disk1

#end


now tit works fine if I substitute $FILE1 and $FILE2 with their absolute values, however when I use the variables instead I get this:


sn0m@sn0m-laptop:~/my_scripts$ sudo ./exp.sh
./exp.sh: line 8: ------------------------------------------------------------------------------: command not found
./exp.sh: line 12: ----------------------------------------------------------------------------: command not found
./exp.sh: line 16: ------------------------------------------------------------------------------: command not found
sending incremental file list
rsync: change_dir "/home/sn0m/$/home/sn0m/back_up" failed: No such file or directory (2)
rsync: change_dir#3 "/home/sn0m/disk1/$/home/sn0m/disk1" failed: No such file or directory (2)
rsync error: errors selecting input/output files, dirs (code 3) at main.c(632) [receiver=3.0.3]
rsync: connection unexpectedly closed (9 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(635) [sender=3.0.3]
./exp.sh: line 21: ----------------------------------------------------------------------------: command not found
sn0m@sn0m-laptop:~/my_scripts$ 



?any help

Thanks in advance

Sokol

---

### Post by heindsight on 2009-01-02
you shouldn't have the $ signs where you are assigning the values of FILE1 and FILE2, change it to:

```

FILE1=/home/sn0m/back_up
FILE2=/home/sn0m/disk1/backup_prova

```

secondly, you may want to remove the ```
----------------------------------------------------------------------------
```
lines, or at least comment them out otherwise you'll always get those command not found errors when running the script

---

### Post by __Ryan__ on 2009-01-02
This should work.

```
#!/bin/bash
#script to back up documents
#Variables
DATE=$(date +%d-%B-%Y)
FILE1=/home/sn0m/back_up
FILE2=/home/sn0m/disk1/backup_prova
#------------------------------------------------------------------------------

/bin/mount -t ntfs /dev/sda4 /home/sn0m/disk1

#----------------------------------------------------------------------------

cd /home/sn0m

#------------------------------------------------------------------------------
#copy experimental folder

/usr/bin/rsync -avz $FILE1/ /home/sn0m/disk1/$FILE2.$DATE

#----------------------------------------------------------------------------
#unmount backup drive

/bin/umount disk1

#end
```

Use the '$' only when referencing variables.

```
VAR=1
echo $VAR
```

The code here has the '$' for a different reason. Whatever is inside the parentheses is executed and the command is replaced by its output. It is not needed for literal strings like your file paths.

```
DATE=$(date +%d-%B-%Y)
```

---

### Post by ushimitsudoki on 2009-01-02
Some tangetially-related points you might find interesting:

1. My favorite bash scripting references:
[Advanced Bash-Scripting Guide]("http://tldp.org/LDP/abs/html/")


2. On Ubuntu, /bin/sh is sym-linked to /bin/dash

Basically, dash doesn't have all the fancy interaction features bash does, so it's better for script execution (but not as good as a user shell).

There are some minor differences between dash and bash, but unless you run into them you might consider a #!/bin/sh shebang, and only specify #!/bin/bash if you are sure you need it. 

If you check most scripts that come with Ubuntu, that's what you'll find.

---

### Post by sn0m on 2009-01-02
Thanks all you guys for your help, much appreciated.
I will certainly have a go at advance bash scripting on my days off.
Coming back to my script:
this is what it looks like at present:

#!/bin/sh
#script to back up documents
#Variables
DATE=$(date +%d-%B-%Y)
FILE1=/home/sn0m/back_up
FILE2=/home/sn0m/disk1/backup_prova
#------------------------------------------------------------------------------

/bin/mount -t ntfs /dev/sda4 /home/sn0m/disk1

#----------------------------------------------------------------------------

cd /home/sn0m

#------------------------------------------------------------------------------
#copy experimental folder

/usr/bin/rsync -avz $FILE1/ /home/sn0m/disk1/$FILE2.$DATE

#----------------------------------------------------------------------------
#unmount backup drive

/bin/umount disk1

#end

this what I get from the command line:

sn0m@sn0m-laptop:~/my_scripts$ sudo ./exp.sh
sending incremental file list
rsync: mkdir "/home/sn0m/disk1//home/sn0m/disk1/backup_prova.02-January-2009" failed: No such file or directory (2)
rsync error: error in file IO (code 11) at main.c(594) [receiver=3.0.3]
rsync: connection unexpectedly closed (9 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(635) [sender=3.0.3]
sn0m@sn0m-laptop:~/my_scripts$ 

emmmmmm, bump
thanks for your help in advance guys
Sokol

---

### Post by heindsight on 2009-01-02
i think your problem here is that mkdir can only create one directory level. in other words if you say
```
mkdir ~/foo/bar
```
and the directory ~/foo does not exist, mkdir will give a 'No such file or directory' error. If you want to create multiple levels of directories use mkdirhier instead. 
```
mkdirhier ~/foo/bar
```
will first check if the directory ~/foo exists (and create it if necessary) before creating ~/foo/bar.

EDIT: i just noticed, mkdir is being called from rsync not from your script, so
perhaps put a line
```
mkdirhier /home/sn0m/disk1/$FILE2.$DATE
``` just before rsync.

---

### Post by ushimitsudoki on 2009-01-02
Use the -p switch to create intermediate paths if needed. Read man pages.

Also check why you have two slashes in a row : "disk1//home"

---

### Post by sn0m on 2009-01-02
thanks for your reply mate.
Directory disk1 already exists in my home directory. It is only used to manually mount hard disk partitions.
 so this is the output:
sn0m@sn0m-laptop:~$ ls
back_up                exp_tag.sh~                   Pictures
bin                    finished_script_run_cron.sh~  Public
convertion_script~     FrostWire                     radio_emig_live.sh~
convertion_script.sh~  Incomplete                    shared_laptop
Desktop                kot                           Templates
disk1                  mary_folder                   themes
disk2                  mpl_tar_experiment.sh~        untitled folder
Documents              Music                         usb
dwhelper               my_scripts                    UsplashFingerprint0.1I386
Examples               new file~                     Videos
exp_tag.sh             Photos
sn0m@sn0m-laptop:~$ 

as you can see disk1 is already there, so when i do sudo mount......./sda4 /home/sn0m/disk1, it gets mounted there.
Ta
Sokol

---

### Post by heindsight on 2009-01-02
wait a second. I just noticed that you're mounting an NTFS filesystem on /home/sn0m/disk1, maybe you should check to make sure it's not being mounted read only.

---

### Post by y@w on 2009-01-02
> **__Ryan__ said:**
> 

The code here has the '$' for a different reason. Whatever is inside the parentheses is executed and the command is replaced by its output. It is not needed for literal strings like your file paths.

```
DATE=$(date +%d-%B-%Y)
```

You can also use backticks if that's a bit more readable (rather than having $ meaning two different things in your code). The line would look like this:

```
DATE=`date +%d-%B-%Y`
```


It's showing that it can't create /home/sn0m/disk1//home/sn0m/disk1/backup_prova.02-January-2009. Is the first part of the path (/home/sn0m/disk1) in there twice on purpose? If not, the rsync line in your code should look like this:

```
/usr/bin/rsync -avz $FILE1 $FILE2.$DATE
```

---

### Post by sn0m on 2009-01-02
thanks y@o
its so stupid of me, obviously I should have put FILE1 instead of part absolute path part variable...
It works fine now.
Many thanks to all you my friends
Regards
Sokol

---

### Post by dagnabit dang doohickey on 2009-01-02
The path handling in the script is arbitrary: paths placed in commands, in variables, and the use of the cd command. This is making the script somewhat confusing. Here's the script slightly cleaned up (but not tested):

```
#!/usr/bin/env bash
#script to back up documents

# variables
DATE="$(date +%d-%B-%Y)"
FILE1_PATH="$HOME"
FILE1_NAME="back_up"
FILE2_PATH="$HOME/disk1"
FILE2_NAME="backup_prova"

# mount backup drive
/bin/mount -t ntfs /dev/sda4 "$FILE2_PATH"

# copy folder to backup drive
/usr/bin/rsync -avz "$FILE1_PATH/$FILE1_NAME" "$FILE2_PATH/$FILE2_NAME.$DATE"

# unmount backup drive
/bin/umount "$FILE2_PATH"
```

---

