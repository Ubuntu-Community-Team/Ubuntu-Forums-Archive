---
title: "Directories to backup"
date: 2009-05-04
forum: General Help
---

### Post by RedSingularity on 2009-05-04
Which directories in / would you recommend backing up every so often?

---

### Post by garythegoth on 2009-05-04
> **Shadow121 said:**
> Which directories in / would you recommend backing up every so often?

I always just backup my personal files to DVD, what else would you want to backup?

---

### Post by RedSingularity on 2009-05-04
Things like settings and preferences within the OS.

---

### Post by CatsRninja on 2009-05-04
in the / folder...mm?


Stuff u altered.
for example i altered a config file of my network, so i backed up that file so i dont have to do the stuff again.
That sort of things.
A new instalation of ur os would replace those files, just backup those you wouldnt want to replace, meaning those you altered.

---

### Post by garythegoth on 2009-05-04
> **CatsRninja said:**
> in the / folder...mm?


Stuff u altered.
for example i altered a config file of my network, so i backed up that file so i dont have to do the stuff again.
That sort of things.
A new instalation of ur os would replace those files, just backup those you wouldnt want to replace, meaning those you altered.

Ok I see, I dont have those kind of issues so please forgive my ignorance :)

---

### Post by CatsRninja on 2009-05-04
> **Shadow121 said:**
> Things like settings and preferences within the OS.

yeah its a bit of a pain to do that manualy each time you do a new install or something goes wrong
(terrebly wrong).
I see you`r asking for especifics,i dont know where the preferences are stored(the especifics anyhow).So i cant help you with that.



Garythegoth, well if you someday have this issues, you know what to do.

---

### Post by Locutus_of_Borg on 2009-05-04
/usr/local
/opt
/etc

are good directories to keep a back-up of

---

### Post by HuckleSmothered on 2009-05-06
I stick with: 
/home/<user name>
/etc

I would also recommend using rsync to do it. Might need to install it. Use this command in a terminal window: 
sudo apt-get install rsync

Here's a sample script similar to what I use. Works great!

> #! /bin/sh

# List of arguments to be excluded
EXCLUDE=--exclude-from=$HOME/.backup/Exclude.list

# Files and folders to be backed up
# A slash '/' on the end will copy the contents
# No slash will copy the entire folder
SOURCE1=/home/<user name>
SOURCE2=/etc
SOURCES="$SOURCE1 $SOURCE2"

# List all options here
OPTIONS="-uvah --delete --ignore-errors --stats"

# Specify the destination of the backup
DESTINATION=/<backup folder>

# Indicate where the log file is to be put
LOG=$HOME/.backup/`date +%b-%0d`.log

# The final command
echo "Beginning Backup at `date +%H:%M_%P`"
sudo rsync $OPTIONS $EXCLUDE $SOURCES $DESTINATION > $LOG
echo "Finished Backup at `date +%H:%M_%P`"

---

