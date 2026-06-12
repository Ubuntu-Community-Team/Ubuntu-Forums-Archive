---
title: "see what file/folder is being written to"
date: 2009-03-14
forum: General Help
---

### Post by jimmy the saint on 2009-03-14
Is there a command that can detail disk io with specifics on which files and folders are currently being written to?  I am trying to identify where certain information is going and there is no documentation to rely on.  Thanks

---

### Post by sdennie on 2009-03-14
There is something called iotop but, it's not in the repos and requires certain kernel features (which I believe the Ubuntu kernels have turned on).  A more detailed but harder to understand way to do this is to tell the kernel to dump block device access to a log:

```

sudo sh -c "echo 1 > /proc/sys/vm/block_dump"

```

Then:

```

tail -f /var/log/syslog

```

To turn off the log spam, use:

```

sudo sh -c "echo 0 > /proc/sys/vm/block_dump"

```

Edit:
Actually, it appears iotop is in the repos as of 8.10:

```

sudo apt-get install iotop

```

Edit again:
Wrong "turn off" flag

---

### Post by heindsight on 2009-03-14
The lsof command lists open files. You could probably try to use that.

The -c option allows you to specify a command (running program) for which open files should be listed.
For example
```
lsof -c firefox
```
will list all the open files for firefox.

The -F option allows you to specify an output format, for use with other programs.
For example
```
lsof -c firefox -Fatn0
```
tells lsof to list all open files for firefox. For each file it will print the 
[LIST]
[*]**a**ccess mode of the file (whether it's open for reading, writing or both)
[*]**t**ype of file (a regular file, a directory, etc) and
[*]**n**ame of the file. 
[/LIST]
The 0 tells it to separate those pieces of information with a NULL character (ascii code 0).

You could combine this with an awk script to get all regular files that a certain program has open.
For example:
```
#!/bin/sh
lsof -c "$1" -Fatn0 | awk -F'\0' '((($1=="aw") || ($1=="au")) && ($2=="tREG")) {print substr($3,2)}'

```

What's happening there is that the output from lsof is being sent to the awk command.
Awk then separates each input lines into 'fields' at the NULL characters (that's what the -F option to awk is for).
Then for each line where the first field ($1) is either "aw" **or** "au" (files that are open for writing or for both reading
and writing) **and** where the second field ($1) is "tREG" (a regular file), awk prints out the third field (the file name)
starting with the second character (because lsof puts an 'n' in front of the file name).

You should try to read the manuals for lsof and awk to get a decent understanding of how all this works.
```
man lsof
man awk
```

---

