---
title: "bash script help"
date: 2005-07-28
forum: Desktop Environments
---

### Post by nvbauer on 2005-07-28
Hellol,

I have this issue, that I though at first was a Mac problem, but now I have tested it on Ubunu and discovered that it is a problem with my script. 

The script itsel is pretty self explanitory. I create a tarball, then use smbclient to shoot it over to a W2K3 share. The code is below:


```
 #!/bin/bash
#####################################################
## ##
## Samba FTP backup V1.2 ##
## script created by Norman V. Bauer ##
## 02/07/2004 ##
## GNU/GPL License 2004 ##
####################################################
# This script allows an admin to backup to a Windows
# Server or Wokstation using FTP or smbclient
# If you use FTP you must have IIS or some other
# webserver with a valid account on the box or Active # directory. For smbclient I used a credentials file
# that stored the log on name and password
# The format of the credentials file is
# username =
# password =
# Please feel free to email me if this was useful
# to you or you have improvements
# nvbauer@myrealbox.com
#
# Credit and thanks to Kevin Wetzel for the FTP section.
# Kevin’s website is http://www.isptoolz.com
#defines the variables for time stamps. Choose your style
SMBSERVER='\\\\Server\\Backups'
WORKGROUP='MYDOMAIN'
PUTPARAMS='PUT /tmp/data-backup.tar.gz mac-backup.tar.gz'
LOCAL='/home/me'
LOCALBUDIR='/tmp'
# Default is DATETIME
DATETIME=`date +%m-%d-%Y-%H%M`

#TIME=`date +%H%M%s` # define a variable for the data
DATA=data-backup

# create a backup log file
 backup_log=/tmp/backup_log
# create a backup error file
backup_err=/tmp/backup_err

# replace old backup logs and create new ones
mv -f $backup_log $backup_log.old

#Give verbose output to log file
echo Starting Backup: $DATETIME   >> ${backup_log}
cd /tmp 
if test -e ${DATA}.tar.gz; then rm ${DATA}.tar.gz echo >> Removed old ${DATA}.tar.gz >>${backup_log}
fi

tar -cpvzf ${LOCALBUDIR}/${DATA}.tar.gz ${LOCAL} 


echo Backup successfuly completed: $DATETIME >>${backup_log}
echo # Backing up to Windows box #>>${backup_log}
echo ____________________________________________>>${backup_log}
echo Starting Samba/FTP session $DATETIME >>${backup_log}
# Uncomment the methode you prefer smbclient or FTP
# Don’t forget to use the “buauth” credential file.
# start a smb session, upload file, get out of there.
# 7/15/04 - added the -W DOMAIN USERS switch. If not included
# smbclient will fail on OS X, SCO, and some minor Linux varriants.
# leaving the switch in will not harm those that do not need it
# If not on a domain simply use USERS or some other local group
#instead.

smbclient ${SMBSERVER} -W ${WORKGROUP}  -A /tmp/bauth -c prompt; cd Mac; ${PUTPARAMS} ; exit;

#Using FTP instead of smbclient
#ftp -in <
#open 172.16.100.2
#user backup backup
#bin
#cd linbackup
#put data-backup.tar
#bye


echo "Samba/FTP session completed ${DATETIME}." >>${backup_log}
echo#################################### >>${backup_log}
echo # Backup operations have ended # >>${backup_log}
echo #################################### >>${backup_log}
exit 0;


```

The Problem is when it gets to the smbclient part. It will connect, then cd into the directory, but then complains about the put command, saying that it does not recognize the command. I tried mput and the same thing happens. I have used put directly and in the form of a variable. 

Interesting enough it works just fine if I do it manualy. 

Any help from you expert bash scripters out there would be greatly appreciated. I think the problem seems to be that it is using the local bash shell rather than the SMB shell. Not sure if that is the case yet and if it is how to chage that. 

Norm

---

### Post by Shiven on 2005-07-28
just guessing here, but why not try the "send" command instead of put...

I can see no problem with the script, then again it is 1am. well i think its 1am :/

maybe someoen else can be a bit more constructive than me at the moment, sorry!

---

### Post by nvbauer on 2005-07-28
I tried send. That did not work either. Thanks for the suggestion.

---

