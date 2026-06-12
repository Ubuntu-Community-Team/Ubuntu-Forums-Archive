---
title: "testing for the existance of a particular file"
date: 2009-03-24
forum: General Help
---

### Post by sofasurfer on 2009-03-24
I learned how to check the existance of a file with "if [ ! -f "$*fullarchive.1.tar" ]; then". I don't remember where I got this.

I later learned from [www.tldp.org](www.tldp.org) about "if [ -f "$*fullarchive.1.tar" ]; then". The differance is the "!".

When using "if [ ! -f "$*fullarchive.1.tar" ]; then", if I delete the file in question the command still shows that it exists.

When using "if [ -f "$*fullarchive.1.tar" ]; then", if I delete the file in question the command shows that it does NOT exist.

Now I create the file and use "if [ ! -f "$*fullarchive.1.tar" ]; then", it shows that the file exists.

But when I create the file and use "if [ -f "$*fullarchive.1.tar" ]; then", it shows that the file does NOT exist.

What am I missing? Why do these commands work in an opposite manner depending on the "!"?

From what I can see, the "!" causes the command the see the file whether it exists or not.

The lack of a "!" causes the command to NOT see the file whether it exists or not.

---

### Post by mcduck on 2009-03-24
The "!" is the logical "not".

if [ -f "$*fullarchive.1.tar" ] tests if the file exists, and if it does, runs the commands

if [ ! -f "$*fullarchive.1.tar" ] tests if the file doesn't exist, and if it doesn't, runs the following commands.

So, both test if the file exists or doesn't, the difference is whether the commands should run if the file exists, or if the file doesn't exist.

---

### Post by sofasurfer on 2009-03-24
O!!
I was trying to figure out how to test for "not" existing. I guess I found it and didn't know it. 

Thank you for answering dumb questions.

I guess its time to start reading [http://tldp.org/LDP/Bash-Beginners-Guide/html/index.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/index.html) from the beginning.

---

### Post by sofasurfer on 2009-03-27
When I run the folloing script it will test whether a filename which contains "fullarchive.1.tar" (such as 271210fullarchive.1.tar) does not exist. The numbers at the beginning of the filename are day-of-month and time stamps. If the file does not exit it will create it. This works fine.

When it is run again it should test whether the file exists and if it does it should create a file such as 271210INCarchive.1.tar, which is the incremental file.

But instead it says that the file still does not exist.

If I replace the $*fullarchive.1.tar in the test command with the full filename of 271210fullarchive.1.tar it will find it. So I think there is a problem with my test command.

Can you tell me what is wrong?

```

#!/bin/sh

#Variables
DOM=`date +%d`                                                                               #Current day of month.. 1-31
HOUR=`date +%H`                                                                                 #Current hour of day.. 1-24    
MIN=`date +%M`                                                                                  #Current minute of hour.. 0-59
TIME=$DOM$HOUR$MIN                                                                           #Current timestamp-day of month + hour + minute
FULLBACKUPFILE=$TIME"fullarchive.1.tar"                                                         #full backup name
INCBACKUPFILE=$TIME"incarchive.2.tar"                                                           #incrementalbackupname 
BACKUPDIR=/media/storage/backup/system-restoration/backup-files/working-system-backup           #backup storage directory  
SNARDIR=/media/storage/backup/system-restoration/backup-files/working-system-backup/snar        #directory for snar (snapshot)         
DIRECTORYNAME=/home                                                                             #directory being backed up

#Move to backup directory
cd /

#Check to see if a full backup has been done
if [ ! -f "$*fullarchive.1.tar" ]; then
 echo "A full backup has not been created."
 read -p &#8220;Press any key&#8221;
 tar cvf $FULLBACKUPFILE --listed-incremental=/snar $DIRECTORYNAME 
 echo $?
elif [ -f "$*fullarchive.1.tar" ]; then
 echo $?
 echo "There is a full backup. Lets do an incremental."
 read -p &#8220;Press any key&#8221;
 tar cvf $INCBACKUPFILE --listed-incremental=/snar $DIRECTORYNAME 
echo $?
else
 echo "The end"
fi

```

---

### Post by lensman3 on 2009-03-27
The program "star" for super-tar is a better backup program than tar.  "star" has similar features of "backup/restore".

---

### Post by sofasurfer on 2009-03-27
I'll go look it up, but I prefer to learn how to succeed with tar first.

---

### Post by Slim Odds on 2009-03-27
> **sofasurfer said:**
> If I replace the $*fullarchive.1.tar in the test command with the full filename of 271210fullarchive.1.tar it will find it. So I think there is a problem with my test command.

You need to understand how bash expands the arguments.

$* expands to the entire command line. Try removing the $

Also, check out the Advanced Bash Scripting Guide. It's good for learning and as a reference
[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

---

### Post by sofasurfer on 2009-03-27
I'll try your suggestion after work tonight. In the meantime, keep those suggestions coming. I'm always open to new things I don't know.

Thanks...

---

