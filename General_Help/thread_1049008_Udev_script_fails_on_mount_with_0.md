---
title: "Udev script fails on mount with 0"
date: 2009-01-24
forum: General Help
---

### Post by dentharg on 2009-01-24
Hi!

I have written a script for me that I want to be started whenever I plug usb disk in.

So in udev I have:
/etc/udev/rules.d/99-backup_on_insert.rules;
```
ATTRS{model}=="WDC WD5000AAKS-0",KERNEL=="sd?", RUN+="socket:/org/freedesktop/hal/udev_event", RUN+="/usr/local/sbin/backup_drive %k"
```

and the script does get started.

In the script I have:

```
mount /dev/sdg1 /mnt/backup/boot
if [ $? -ne 0 ]; then
  logger "Mounting boot failed with $?"
  exit 0
fi
```

and in syslog I have exactly the line:
  "Mounting boot failed with 0"

However when I start this script by hand from console everything runs smoothly.

---

### Post by dcstar on 2009-01-24
> **dentharg said:**
> Hi!

I have written a script for me that I want to be started whenever I plug usb disk in.

So in udev I have:
/etc/udev/rules.d/99-backup_on_insert.rules;
```
ATTRS{model}=="WDC WD5000AAKS-0",KERNEL=="sd?", RUN+="socket:/org/freedesktop/hal/udev_event", RUN+="/usr/local/sbin/backup_drive %k"
```

and the script does get started.

In the script I have:

```
mount /dev/sdg1 /mnt/backup/boot
if [ $? -ne 0 ]; then
  logger "Mounting boot failed with $?"
  exit 0
fi
```

and in syslog I have exactly the line:
  "Mounting boot failed with 0"

However when I start this script by hand from console everything runs smoothly.

Do not make the assumption that because something runs in a user shell environment it will run in another environment.

Check any udev HOWTOs on what you need to do to make these sort of things function.

---

### Post by heindsight on 2009-01-24
> **dentharg said:**
> Hi!

I have written a script for me that I want to be started whenever I plug usb disk in.

So in udev I have:
/etc/udev/rules.d/99-backup_on_insert.rules;
```
ATTRS{model}=="WDC WD5000AAKS-0",KERNEL=="sd?", RUN+="socket:/org/freedesktop/hal/udev_event", RUN+="/usr/local/sbin/backup_drive %k"
```

and the script does get started.

In the script I have:

```
mount /dev/sdg1 /mnt/backup/boot
if [ $? -ne 0 ]; then
  logger "Mounting boot failed with $?"
  exit 0
fi
```

and in syslog I have exactly the line:
  "Mounting boot failed with 0"

However when I start this script by hand from console everything runs smoothly.

In bash, $? always contains the exit status of the last command executed. If you read the bash help for the if command, you'll see that the syntax is:
```
if COMMANDS; then COMMANDS; fi
``` and that the 'then' COMMANDS are executed only if the exit status of the 'if' COMMANDS is 0 - In other words, if you reach the first command after then, $? is always 0.

So to get a slightly more useful return code from mount in your output, I would recommend doing something like:
```
mount /dev/sdg1 /mnt/backup/boot
stat=$?
if [ $stat -ne 0 ]; then
  logger "Mounting boot failed with $stat"
  exit 0
fi
```

---

