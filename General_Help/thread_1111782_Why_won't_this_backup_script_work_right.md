---
title: "Why won't this backup script work right?"
date: 2009-03-31
forum: General Help
---

### Post by sofasurfer on 2009-03-31
In the following script, the first step is to check if a full backup has been created by testing for the existance of a file that contains "*fullarchive.1.tar", where "*" would be $TIME. If a full backup has NOT been created, tar creates it. This part works fine.

When it is run a second time, it should see that the full backup has been created and then a incremental backup will be created.

However, the second run says that the full backup still has not been created.

Can anyone see what is wrong?

I suspect that the problem is in the command... 
if [ -f $*fullarchive.1.tar ].

Apparently there is a problem with using wildcards. 
If I change the filename to the actual name that was created, such as "$310437fullarchive.1.tar" it will work fine.
I tried eliminating the "$" and also adding quotes around the filename. Nothing seems to work.

```

#!/bin/sh
# full and incremental backup of /home directory. Soon to be changed to do a full system  backup

#Written from ideas learned at https://lists.ubuntu.com/archives/ubuntu-users/2008-May/147386.html

#Change the variables below to fit your preferences

#Variables

#Current day of month.. 1-31
DOM=`date +%d`                                                                                  
#Current hour of day.. 1-24
HOUR=`date +%H`                                                                                     
#Current minute of hour.. 0-59
MIN=`date +%M`                                                                                  
#Current timestamp-day of month + hour + minute
TIME=$DOM$HOUR$MIN                                                                           
#full backup name
FULLBACKUPFILE=$TIME"fullarchive.1.tar"                                                         
#incrementalbackupname
INCBACKUPFILE=$TIME"incarchive.2.tar"                                                           
#backup storage directory 
#BACKUPDIR=/media/storage/backup/system-restoration/backup-files/working-system-backup  
BACKUPDIR=/           
#directory for snar (snapshot) 
#SNARDIR=/media/storage/backup/system-restoration/backup-files/working-system-backup/snar
SNARDIR=/snar                 
#directory being backed up
DIRECTORYNAME=/home                                                                             

#Move to backup directory
cd /
#Check to see if a full backup has been done
 if [ -f $*fullarchive.1.tar ]; then
 echo "Full backup exists"
 read -p &#8220;Press any key to create an incremental backup&#8221;
 cp /snar /snar-1
 tar cvf $INCBACKUPFILE --listed-incremental=$SNARDIR $DIRECTORYNAME
fi
 echo "A full backup has not been created."
 read -p &#8220;Press any key&#8221;
 tar cvf $FULLBACKUPFILE --listed-incremental=$SNARDIR $DIRECTORYNAME 
 echo $?
fi

```

---

### Post by sofasurfer on 2009-04-01
Bump

---

### Post by WilliamJenningsBryan on 2009-04-01
You're right that it has to do with the wildcard. You just can't pass a wildcard in that context, if -f expects an absolute name/list.

Maybe try adding a step using ls *fullarchive.1.tar to get the file name.

---

