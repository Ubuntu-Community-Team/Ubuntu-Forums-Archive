---
title: "Dino's revolving daily mysql backup script"
date: 2009-04-08
forum: General Help
---

### Post by kooldino on 2009-04-08
I wrote a 7 day revolving backup script for the mysql database that runs a small wiki that I run.  I figured I'd share it.  This can be modified to do a 7-day revolving backup of anything.

I set my /etc/crontab file to call this script every night at midnight with the following line:

```
0 0     * * *   root    /mysqlbackups/revolve/revolve.sh

```

The permissions of this file should be set to 711 so that no one can see your password or other sensitive information in the file.

[COLOR="Red"]WARNING: This DOES require that the backups are all kept in a directory that contains nothing else.  If it does not, it could delete files unintentionally.
[/COLOR]
If you make improvements to this script, feel free to post them here.

```
#!/bin/bash
#By Kooldino
#This backup file assumes that you will have a backup directory that contains nothing but the script
#and the backup files.

#You can change the backup directory  below to the one of your choice.
cd /mysqlbackups/revolve

#Figure out what to name this backup file
        this_backup_file="wikidb_"
        this_backup_file=$this_backup_file"$(date +%a_%m_%d)"".sql"
        echo
        echo This backup file will be called: $this_backup_file
#/Figure out what to name this backup file

#Figure out the day of the week
        today="$(date +%a)"
        echo Today is $today
#/Figure out the day of the week

#Find and delete the last sql file with the same day of the week
        ls -al wiki*$today*.sql --time-style=+%a | awk '{ print "The last backup from a "$6,"is named: " $7 }'
        file_to_delete="$(ls -al wiki*$today*.sql --time-style=+%a | awk '{ print  $7 }')"
        echo The file I\'m deleting is: $file_to_delete
        rm -f $file_to_delete
#/Find and delete the last sql file with the same day of the week


#Backup the database and copy it to the new raid
mysqldump -u yoursqlusername -pyourpassword wikidb > $this_backup_file
cp -p $this_backup_file /newraid/wiki_backup/daily/
echo

```

**Things you may want to change:**

-yoursqlusername - this should be set to your mysql username

-yourpassword - your mysql password.  Note that there is no space between this and the "-p"

-/mysqlbackups/revolve - Change this to whatever directory you want to have as the dedicated backup directory

Obviously I can tweak this script and just use variables that you define in the top of the file, but I've already done the dirty work for you, so be happy with what you've got.
:p

Enjoy.

---

### Post by kooldino on 2009-04-09
This is a good how-to for people who need database backups.

---

### Post by kooldino on 2009-04-27
:bump:

---

### Post by kooldino on 2010-02-04
Bump!

---

