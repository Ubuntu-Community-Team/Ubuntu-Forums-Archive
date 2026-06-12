---
title: "How to open a pop up window with a drop down list from a script"
date: 2014-10-17
forum: Desktop Environments
---

### Post by actionmystique on 2014-10-17
Environment: Ubuntu 14.04

Hello guys,

I've written a simple script that runs automatically every night to backup all my hard drive:
```
...
**today**=$(date +%A)
fsarchiver -j6 -v -o -A savefs /mypath/MSI-GE60-Ext4-**$today**.fsa $msiext4
```

The script writes the backup with the current day at the end of each filename.

I'd like to complete the restore script so that it prompts a pop up window offering a drop down list containing all the days of the week so that the user can choose which backup is to be restored.

Is there a simple way to do that?

---

### Post by buzzingrobot on 2014-10-17
Research 'zenity', a toolkit designed for that sort of thing.

---

### Post by actionmystique on 2014-10-17
Thanks! I'll take a look into it.

---

### Post by actionmystique on 2014-10-17
Great! Here's one solution:

```
#!/bin/bash
...
**day**=$(zenity  --list  --radiolist --column "Pick" --column "Day" TRUE Monday FALSE Tuesday FALSE Wednesday FALSE Thursday FALSE Friday FALSE Saturday FALSE Sunday)

umount /media/...
fsarchiver -j6 -v restfs /media/mypath/MSI-GE60-Ext4-**$day**.fsa id=0,dest=$msiext4
```

---

