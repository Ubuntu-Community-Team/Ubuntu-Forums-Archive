---
title: "How do I get a count of how many times a file is accessed?"
date: 2009-04-09
forum: General Help
---

### Post by jimbren on 2009-04-09
I'm trying to determine how many times a set of files is accessed within a given time frame.  I don't need to now specific times a file is accessed, just how many times the files have been accessed.  Can you help?

thanks,

jim

---

### Post by dcstar on 2009-04-09
> **jimbren said:**
> I'm trying to determine how many times a set of files is accessed within a given time frame.  I don't need to now specific times a file is accessed, just how many times the files have been accessed.  Can you help?


AFAIK only specific things like web servers will log individual file accesses, and post-processing of these logs will give you a count.

I don't know of anything that counts file accesses, even the default file system updating of access times puts an additional load on a system and I don't want to think what extra load keeping track of each access would do!

---

### Post by amac777 on 2009-04-09
To monitor file access you can use the inotifywatch command. You will need to first install the inotify-tools package as follows:

```
sudo apt-get install inotify-tools
```

Then, for example, say you want to monitor the file /home/user/file.txt for 30 seconds, you can use this command:

```
inotifywatch -t30 /home/user/file.txt
```

After 30 secons, it will output a table summarising all accesses of that file. For example:

```
Finished establishing watches, now collecting statistics.
total  access  close_nowrite  open  filename
6      2       2              2     /home/user/file.txt

```

That means the file was read twice. 

There are lots of options for the inotifywatch command and it will also monitor directories recursevely or lists of files. If you don't want to first specify the time, you can just press control-C to stop monitoring and display the results. You can also limit it only to watch for specific types of access only (like reads or writes etc). To read about the command, see the man page:

```
man inotifywatch
```

---

