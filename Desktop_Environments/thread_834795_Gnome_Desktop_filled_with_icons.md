---
title: "Gnome Desktop filled with icons"
date: 2008-06-19
forum: Desktop Environments
---

### Post by skaliann on 2008-06-19
Hi,

I invoked Disk Usage analyzer(baobab) to scan my home directory. My home directory has .snapshot directory which has  hourly/nightly snapshot directories of my home directory.

I have two issues, 
how do i exclude .snapshot from being scanned?

After i invoked baobab, I had to kill the process and now my entire Desktop is filled with icons for all the files in my .snapshot directory.

For e.g, my HOME looks like
~/xx
~/yy
~/.snapshot/hourly.0/xx
~/.snapshot/hourly.0/yy
~/.snapshot/hourly.1/xx
~/.snapshot/hourly.1/yy

Now I have 4 icons for the above directories in my Desktop. But ~/Desktop/ doesn't have those directories or links to them. I'm not sure how or why the icons are showing without any corresponding entries in ~/Desktop.

I tried logging out but it didn't help.
My entire desktop is filled with icons. Please help me remove them

thanks
Suresh

---

### Post by VMC on 2008-06-19
Open a terminal and type the following

```
ls ~/Desktop
```

Then you can tell us which ones you want removed. You can use a "greedy" character to help remove them.

---

### Post by skaliann on 2008-06-19
Ok. `killall nautilus` fixed the icon problem.

I still need to know how to exclude certain directories being scanned by baobab

thanks
Suresh

---

### Post by Happy_Man on 2008-06-19
Is your /home on a separate partition? If so, then you can exclude that partition from being scanned in Edit --> Preferences.

---

### Post by skaliann on 2008-06-20
I do want to scan my home directory. But exclude certain folders within my home directory.

Suresh

---

