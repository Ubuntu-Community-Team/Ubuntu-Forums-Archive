---
title: "How to get recursive count of items in a directory"
date: 2009-04-27
forum: General Help
---

### Post by MountainX on 2009-04-27
I'm looking for a command or shell script to show, for each directory 1 level below the current, the total count of all items in the said directory (and all the subdirectories under it).

How can this be done?

I think it would be similar to something like this, but for item count, not size:
```
du --max-depth=1 /path/ | sort -n -r 
```

---

### Post by trwww on 2009-04-27
For each directory in the current directory, print the directory name and then the number of files contained in the given directory and that directory's children:

[FONT="Courier New"]for mydir in `find * -type d -maxdepth 1`; do echo -n "$mydir: "; find $mydir -type f | wc -l; done[/FONT]

---

### Post by MountainX on 2009-04-27
Thank you!

---

### Post by MountainX on 2009-04-27
```
for mydir in `find * -maxdepth 1 -type d`; do echo -n "$mydir: "; find $mydir -type f | wc -l; done
```

---

