---
title: "Not able to access synaptic package manager"
date: 2009-01-19
forum: General Help
---

### Post by empireruler on 2009-01-19
I am running ubuntu 8.10, and have recently started getting a message while trying to run synaptic, update, or add/remove programs:
E: Encountered a section with no Package: header
After trying to find a way to get around that, I looked online and found the code:
```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.old
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo aptitude update
```
After running this I now get this message:
E: Unable to parse package file /var/lib/dpkg/status (1)
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.
I have tried sudo dpkg clear-avail as well, but to no avail.
I am running ubuntu on an AMD 64 computer.
Could somebody please help me... I am a beginner so would need the code posted.
Thanks.

---

### Post by drs305 on 2009-01-19
First let's put things back the way they were:

```

sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.1
sudo mv /var/lib/dpkg/status.old  /var/lib/dpkg/status

```

Then try moving this folder, recreating it and running the update:
```

sudo mv /var/lib/apt/lists $HOME/Desktop/lists
sudo mkdir /var/lib/apt/lists /var/lib/apt/lists/partial
sudo aptitude update

```

---

### Post by empireruler on 2009-01-20
When I ran those codes I got this
```
Reading package lists... Error!
E: Unable to parse package file /var/lib/dpkg/status (1)
E: The package lists or status file could not be parsed or opened.
E: Couldn't rebuild package cache
E: Unable to parse package file /var/lib/dpkg/status (1)
E: The package lists or status file could not be parsed or opened.

E: Unable to parse package file /var/lib/dpkg/status (1)
E: The package lists or status file could not be parsed or opened.

```
I do not know if this is related... but the gnome bar at the top of ubuntu is only showing a part of it, with the rest being cut off.

---

### Post by drs305 on 2009-01-21
For now, put things back the way they were:
```
sudo cp -r $HOME/Desktop/lists /var/lib/apt/lists
```
Everything should now be back the way it was before you made any changes except for the "dpkg --clear-avail" command.

Have you tried running the "dpkg - Repair broken packages" option from the recovery mode?

If the recovery mode fix doesn't work, I have one more suggestion. Backups are kept in /var/backups. You may have older copies of the *status* file in that folder, compressed as dpkg.status* . If they aren't too outdated, you could try extracting an older *status* file and replacing the current one. Make a backup of the current /var/lib/dpkg/status file first.

You can also save a list of your existing packings to the Desktop with this:
```

dpkg --get-selections > $HOME/Desktop/dpkg.list

```
To restore the list, if necessary:
```

sudo dpkg --clear-selections
sudo dpkg --set-selections < $HOME/Desktop.dpkg.list

```

---

### Post by aqb on 2009-04-20
thanks a lot, i had the same type of problem. All i had to do was replace the backup copy of the status file with the current one.

:D:D:D:D:D

---

