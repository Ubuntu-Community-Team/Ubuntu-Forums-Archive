---
title: "help  please in terminal with find and delete"
date: 2009-07-23
forum: Desktop Environments
---

### Post by m_ghv_geo on 2009-07-23
hi all i need help with terminal lets say in the folder called "xxx" are many sub folders and in those sub folders are  more sub folders and in those folders are music with .mp3 format and are pictures with .jpg and lets say i want to delete any picture with .jpg ALL of them 
if they were in one folder i would use rm "*.jpg" but in that condition i do  not know what command or commands to use
am sure am prete close i did something like this i went with terminal in "xxx" folder and execute comand     # find . -name  "*.jpg" > jpg-list.txt
but after that i do not know what to do:confused:

---

### Post by kaibob on 2009-07-24
The following site has a lot of good information on the find command:

[http://content.hccfl.edu/pollock/Unix/FindCmd.htm](http://content.hccfl.edu/pollock/Unix/FindCmd.htm)

The following are three examples from this site that delete files:

```
find /directory/path -name core | xargs /bin/rm -f
find /directory/path -name core -exec /bin/rm -f '{}' \; # same thing
find /directory/path -name core -delete                  # same if using Gnu find
```

I believe the second of the above commands will handle files with spaces and is probably the one I would use to bulk delete files.

---

### Post by Dullstar on 2009-07-24
You can always do it through the file manager.

---

### Post by DaithiF on 2009-07-24
similar to reply above, but since you can't specify a single filename you need to use a wildcard, and to avoid the shell expanding the wildcard character before it runs the find command you need to enclose the name pattern in quotes.  So:
find /directory/path -name '*.jpg' -exec rm -f '{}' \;

if you want to be super careful and preview what files this will match before deleting them,  then run the above but with echo instead of rm -f.  So: 
find /directory/path -name '*.jpg' -exec echo '{}' \;

if you are happy with the list this produces, then run the first command

---

### Post by m_ghv_geo on 2009-07-25
thanks all a special to :KS-->DaithiF<--:KS i used   # find -name '*.jpg' -exec rm -f '{}' \;
in the my xxx folder it did a nice job i had 37 sub folders and more than 1000 files it would take my a yer to delete one by one  but the command line is  fester in things like this
and for the point i used in my iphone-s terminal

---

### Post by m_ghv_geo on 2009-07-25
> **Dullstar said:**
> You can always do it through the file manager.
what do you mean with  file manager ? witch   file manager?

---

