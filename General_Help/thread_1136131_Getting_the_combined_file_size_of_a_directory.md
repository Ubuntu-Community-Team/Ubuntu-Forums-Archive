---
title: "Getting the combined file size of a directory"
date: 2009-04-24
forum: General Help
---

### Post by pan69 on 2009-04-24
OK. Say I'm in my home directory. I now what to know how much disk space all the files in my home directory are taken up. What would be the command to do this? 

I've been looking around but I can't really find anything. I assume I'm not using the correct keywords when searching...

Any help would be appreciated.

- Luke

**UPDATE:**

Sorry guys. I should have explained better. My bad. I'm not looking for disk analyzing tools, just a simple command line instruction that will tell me the total size of all the files in the directory I run the command on. You know, like the 'dir' command in DOS used to do. I was expecting that 'ls' would be able to do this but that doesn't seem to be the case.

**UPDATE 2:**

It seems that the 'du' command seems to do something. It's quite verbose though...

**UPDATE 3:**

'du -hs' seems to do exactly what I want. Thanks everyone who replied!

---

### Post by Bakon Jarser on 2009-04-24
Applications > Accessories > Disk Usage Analyzer

It's a great tool.  For better search results see the link in my sig.

---

### Post by MountainX on 2009-04-24
Are you using the Ubuntu Desktop (gnome)? If so, open "Places > Home Folder" and right click Home Folder, choose properties, and it will total up the size of the contents for you.

---

### Post by MountainX on 2009-04-24
See this too:
[http://www.linux.com/feature/51600](http://www.linux.com/feature/51600)
```
$ df -h -T
$ du -ah | sort -n
```

---

### Post by Bakon Jarser on 2009-04-24
ls -l -h

to also sort by file size

ls -l -h -S

the s has to be capital

---

### Post by pan69 on 2009-04-24
> **Bakon Jarser said:**
> ls -l -h

to also sort by file size

ls -l -h -S

the s has to be capital

Hmmm. 'ls' seems to list the combined file size first which is almost always of screen. I can't seem to get rid of the file listing since I'm just after the total. I also get the impression that 'ls -lh' doesn't include any sub directories, adding -R to it (ls -Rlh) seems to do that but again, it's lists all the file entries so my total is again of screen. I probably could grep it but that's to much typing...

I'm sticking with 'du -hs' for now.

---

### Post by Bakon Jarser on 2009-04-25
```
ls -Rlh | more
```

That will display the output one page at a time.  Press space bar to advance to the next page or enter to advance to the next line and q to quit.  It seems like the -d function doesn't do anything.  I though it was supposed to only display directories but I get no useful output in any folders with that option.  Is this a bug?

Edit:  I don't think this can be done with ls.  Strange, seems like it would be a useful feature.

---

