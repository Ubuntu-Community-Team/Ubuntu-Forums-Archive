---
title: "View non default packages in Synaptic"
date: 2009-05-29
forum: General Help
---

### Post by cmwslw on 2009-05-29
I've recently been going on a cleaning rampage for my computer. Synaptic makes things really easy, but I'd like to know how to set up a filter that shows non-default packages. What I mean by this is the packages that were installed that are not included in the default packages of Jaunty. Is there any way I can do this. I'm sure I've installed some extra programs that I don't need anymore.

---

### Post by unutbu on 2009-05-29
Open a terminal and type
```
grep ' installed' /var/log/dpkg.log* > installed.txt
```

The file installed.txt will contain a list of all the packages you've installed with Synaptic.

There will be duplicates in installed.txt, if you want a list of packages with no duplicates, run this:```


grep ' installed' /var/log/dpkg.log* | awk '{print $5}' | sort | uniq > uniq-installed.txt
```
The list will be in the file called uniq-installed.txt

---

### Post by cmwslw on 2009-05-29
> **unutbu said:**
> Open a terminal and type
```
grep ' installed' /var/log/dpkg.log* > installed.txt
```

The file installed.txt will contain a list of all the packages you've installed with Synaptic.

There will be duplicates in installed.txt, if you want a list of packages with no duplicates, run this:```


grep ' installed' /var/log/dpkg.log* | awk '{print $5}' | sort | uniq > uniq-installed.txt
```
The list will be in the file called uniq-installed.txt

That includes the ones installed with a default Ubuntu installation. I only want to see the extra ones. Also, that does not include the ones installed via the terminal.

---

### Post by unutbu on 2009-05-29
Well, you could look in /var/log/dpkg.log*. Notice that the datetime when each package was installed is recorded. Look in /var/log/dpkg.log.# where # is the largest number. That is the oldest log file. If you were to cut out all the lines that are timestamped when you first installed, then everything that is left is obviously stuff you must have installed manually later.

You could copy all the log files with

cp /var/log/dpkg.log* /tmp

and then edit a copy of the last log file. Then process them as suggested above.> 

Also, that does not include the ones installed via the terminal. 

I don't know about aptitude, but if you installed packages with apt-get, then they will show up in /var/log/dpkg*.

---

### Post by cmwslw on 2009-05-29
> **unutbu said:**
> Well, you could look in /var/log/dpkg.log*. Notice that the datetime when each package was installed is recorded. Look in /var/log/dpkg.log.# where # is the largest number. That is the oldest log file. If you were to cut out all the lines that are timestamped when you first installed, then everything that is left is obviously stuff you must have installed manually later.

You could copy all the log files with

cp /var/log/dpkg.log* /tmp

and then edit a copy of the last log file. Then process them as suggested above.
I don't know about aptitude, but if you installed packages with apt-get, then they will show up in /var/log/dpkg*.

Doing that might be confusing since I have upgraded from Intrepid; that means I would have packages installed before the Jaunty upgrade. I guess what would help would be a complete list of the **default** Jaunty packages. Then I could compare what I have to that using diff.

---

