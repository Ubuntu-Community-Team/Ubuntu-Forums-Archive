---
title: "Problems chmoding a ton of directories"
date: 2005-04-11
forum: Desktop Environments
---

### Post by Jump on 2005-04-11
I want to be able to manage my personal files (ie deleting, renaming, etc.) without having to do everything in the terminal with a command line. Is there a way to accomplish this? I know I can chmod a directory but I have like 500 directories pulled from an old Windows box and I want to manage them more easily through Gnome's file manager (ie. right click rename etc.) and I can't figure out how to chmod not only the directory, but all the directories within it. A temporary root account would be perfect.

---

### Post by alainhenry on 2005-04-11
I am not sure I understand your problem, but if you want a "temporary root", you can open a root terminal from "system tools" menu, and use chmod with -R option 
see this
[http://www.linuxdevcenter.com/linux/cmd/cmd.csp?path=c/chmod](http://www.linuxdevcenter.com/linux/cmd/cmd.csp?path=c/chmod)
for chmod help 

Alain

---

### Post by Jump on 2005-04-11
I figured it out. I was looking for the chown -R command. Now that its under my name instead of root I can do all the renaming etc i needed.

---

### Post by nmsa on 2005-04-11
I can suggest two directions:  :| 

1. use the terminal, make a small script and chown and chmod as you like.
 the script can look like this:
 #!/bin/sh
 #list the content of current dir in a variable
 for i in `ls -R`
 do
  #print out the current dir
  echo $i
  # change some attributes
  chown xxx:yyy $i
  chmod a+rx $i
  #wait a few seconds
  sleep 3
 done

 replace xxx and yyy and a+rx with the attributes you may need

2. if your box Internet ready go to net2ftp.com and check chmod feature

I know is a hard w/a but I don't think nautilus can help with recursive operations on directories.

---

### Post by skoal on 2005-04-11
Open a terminal, and go to any directory and do the following:

```
find . -type d -exec chmod xyz {} \;
```

* replace 'xyz' with the permissions you want.  For example: xyz=770.  That will replace all {sub}directories with those permissions.  If you want to change the owner.group settings as well, change the 'chmod' stuff to 'chown user.group {} \;' (replacing user.group with who you want).

---

### Post by lynng on 2005-09-28
Thanks skoal, I had been trying to pipe the output of a find cmd to chmod.

I was able to use
```
find . -type d -exec chmod 770 {} \;
find . -name *.mp3 -exec chmod 644 {} \;
```
to change perms for a bunch of files stored on a shared fat32 partition.

---

