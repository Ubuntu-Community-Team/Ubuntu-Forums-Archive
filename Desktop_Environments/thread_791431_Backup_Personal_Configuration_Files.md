---
title: "Backup Personal Configuration Files"
date: 2008-05-12
forum: Desktop Environments
---

### Post by john_markh on 2008-05-12
After I had couple of system crashes, my GNOME configuration were not usable anymore (corrupted files). After number of attempts I've deleted GNOME configuration just to be able to login, I had to reconfigure many applications (Evolution, Network Manager, Nautilus, etc.)
I've decided to write a small script to backup important files. First of all, I've created .backup directory. 
```
mkdir  ~/.backup
```
Then, in .backup directory I've created a file which contain the list of directories needed to backup.
```
 gedit ~/.backup/backup.list
```
```
.config
.gconf
.gconfd
.gnome2
.gnome2_private
.gnupg
.evolution
.nautilus
```
Finally, a small bash script to create compressed tar archive
```
gedit ~/.backup/backup.sh
```
```
#!/bin/bash

# create backup prefix and suffix using date command
preffix=$(date +%F) # %F   full date (same as %Y-%m-%d)
suffix='.tar.gz'

# create backup using compressed tar
tar pzcf ~/.backup/$preffix\_backup$suffix -T ~/.backup/backup.list
```

That's it.
To use the script, all you have to do is to make it executable
```
chmod +x .~/.backup/backup.sh
```
and run it
```
~/.backup/backup.sh
```

If someone has know which other directories need to be backed up, please...

---

### Post by chandra on 2008-05-12
Assuming that personal config files all start with dot (.) as their first character and a letter as the second character, if instead of
```
tar pzcf ~/.backup/$preffix\_backup$suffix -T ~/.backup/backup.list
``` 
you had
```
tar pzcf ~/.backup/$preffix\_backup$suffix ~/.[a-z][A-Z]*
```
I think it would be more comprehensive.

This solution is not foolproof because directories like .mozilla/firefox, and .mozilla-thunderbird, contain more than configuration information. Exclude whatever is unnecessary by using the
```
--exclude=PATTERN
```
option.

---

