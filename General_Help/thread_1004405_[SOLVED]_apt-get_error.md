---
title: "[SOLVED] apt-get error"
date: 2008-12-07
forum: General Help
---

### Post by replab_robin on 2008-12-07
I have installed 8.10 on an MSI Wind for about 1 week. Have adjusted hardware and updated several times with no problem, but today after installing iasl (for debugging dsdt problems) I saw this error coming out of synaptic.

After killing the updater and fixing up locks I find that something seems to be wrong with apt/dpkg. Basically the error I see looks like

E: Problem parsing dependency Recommends
E: Error occurred while processing netbase (NewVersion1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

this happens when I try to update. 

I have googled for this and it seems similar problems have occurred before. I tried fixing /var/lib/apt by removing the lists (as suggested in the past), but nothing I do seems to fix the problem.

So far as I know I have not altered anything in /etc/apt so I presume I'm running stock sources.

---

### Post by fooman on 2008-12-07
try running this in a terminal:

```
sudo dpkg --configure -a
```

see if that helps.

---

### Post by replab_robin on 2008-12-07
> **fooman said:**
> try running this in a terminal:

```
sudo dpkg --configure -a
```

see if that helps.
 this is what I get

robin@maxikat:~$ sudo dpkg --configure -a
dpkg: parse error, in file `/var/lib/dpkg/status' near line 5959 package `netbase':
 `Conflicts' field, reference to `inetutils-inetd': version contains ` '
robin@maxikat:~$

looks to me like a bad status file or something. Any idea how I fix that?

---

### Post by drs305 on 2008-12-07
Here are a couple of 'hacks' that could work:

**In either case, make a backup of the 'status file':**
```

sudo cp /var/lib/dpkg/status /var/lib/dpkg/status-original

```
1. Replace /var/lib/dpkg/status with status-old:
```

sudo mv /var/lib/dpkg/status /var/lib/dpkg/status-temp
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo apt-get update

```

If that doesn't work, restore original:
```

sudo rm /var/lib/dpkg/status
sudo cp /var/lib/dpkg/status-temp /var/lib/dpkg/status

```

2. Edit the status file:
```

gksudo gedit #5959 /var/lib/dpkg/status

```
Gedit will open at line 5959. This is where part of the problem lies. Remove that entire section, beginning with the line that starts with "Package: " and ends with a line break.

If that doesn't work, restore original:
```

sudo rm /var/lib/dpkg/status
sudo cp /var/lib/dpkg/status-original /var/lib/dpkg/status

```

---

### Post by replab_robin on 2008-12-07
OK number 1 seems to work. Any idea how this could happen?

---

### Post by drs305 on 2008-12-07
> **replab_robin said:**
> OK number 1 seems to work. Any idea how this could happen?

Well, the error message says there was a problem in the Conflicts line. Whether is was a punctuation error or something more significant I couldn't tell you without looking at the file. How the line became corrupted is anyone's guess. 
```
dpkg: parse error, in file `/var/lib/dpkg/status' near line 5959 package `netbase':
`Conflicts' field, reference to `inetutils-inetd': version contains ` '

```

Replacing the current file with the default backup (status-old) seems to have done the trick. I added the second possible fix because oftentimes in the user's attempts to fix the corrupted status file he/she has already taken steps which will have changed the status file and thus moved the error into the backup as well.

---

### Post by replab_robin on 2008-12-07
Well after having fixed the original problem I suddenly started getting strange errors eg lockups and strangekeyboard issues. It may be that my hdd & wifi card swaps weren't actually all that successful. I don't know anything in ubuntu that could cause the uppercase led to start flashing. So I guess it was my hardware.

Luckily the original hardware seems to work fine (win xp hdd &rtl8187se) so I've swapped back to that while I get more info.

---

