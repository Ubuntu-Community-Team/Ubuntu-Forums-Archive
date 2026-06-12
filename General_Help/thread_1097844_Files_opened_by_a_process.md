---
title: "Files opened by a process"
date: 2009-03-16
forum: General Help
---

### Post by jdavidw13 on 2009-03-16
I'm wondering if there is a way to show all files ever opened by a process during its lifetime.  I understand I could use lsof or ls /proc/<pid>/fd to see files that are currently opened, but I'm looking for all files ever opened by the process.  Is this information even available?  Thanks!

---

### Post by heindsight on 2009-03-16
You can also use
```
lsof -p PID
```
To see all files a process currently has open.

I don't believe there's a way to list all files a process ever had open though -  I just don't think this information is recorded anywhere.

---

### Post by jdavidw13 on 2009-03-16
I was afraid that was the case.  Thanks anyways!

---

### Post by heindsight on 2009-03-16
I may be wrong though.
It's possible that there exists some sort of process accounting software that can record/report on all files ever opened by a process. I wouldn't know where to start looking though.

What you could perhaps do (although it's tedious and by no means foolproof) is something like:

```
#!/bin/sh

"$@" &
P=$!
lsof -p $P +r 1 > $P.opened_files

```

This script will launch the program specified on the command line, get it's process id and then run lsof in repeat mode. lsof will then repeatedly (once per second) list all files opened by the process (until there are no more open files). This list will be output to a file, which you could then later process to get a list of all the files the process opened (at least the ones that weren't closed within less than a second of opening). OF course many files will be listed multiple times, so it would probably require quite a bit of processing to get the final list of files...

---

