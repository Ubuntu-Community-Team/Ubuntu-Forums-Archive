---
title: "Error installing Americas Army"
date: 2006-01-20
forum: Gaming &amp; Leisure
---

### Post by TheIdiotThatIsMe on 2006-01-20
I have downloaded the .run file to install Americas Army as stated by the [Wiki]("https://wiki.ubuntu.com/AmericasArmy") but ran into the following error on install:

```
loki_setup: Read failure on armyops250.tar.bz2

```

I have no idea what to do :confused:

---

### Post by jon_z on 2006-01-20
that file appears to be zipped, in order for it to be installed the ending must be .run

in a terminal in the directory where armyops250.tar.bz2 is do the following:

```
tar jxf armyops250.tar.bz2
```

that should unzip it to the run file, then proceed to run the loki command. Hope that helps

---

### Post by TheIdiotThatIsMe on 2006-01-20
The file I have is armyops250-linux.run

I use: 

```
 sudo sh ./armyops250-linux.run
```

Then the loki installer pops up, I click install, and it begins to install some files and then gives me that error.

---

### Post by jon_z on 2006-01-20
sounds like it is a bad download, try from a different source, if thats not it, im not too familiar with A.A. to help you.

---

### Post by TheIdiotThatIsMe on 2006-01-20
I thought it might have been a bad download but it passes the archive integrity check :confused:

---

### Post by Tichondrius on 2006-01-23
it might be because you don't have enough disk space so the self extracting .run file is not able to self extract. Are you running on low disk space ?  (use "df ." to find out)

---

### Post by Kenza on 2008-10-21
Well i got AA to start installing here, but i'm having problems when it gets to the default directory it installs to, I have got root permission on terminal although when i go to install game it says i don't have permission still.

---

