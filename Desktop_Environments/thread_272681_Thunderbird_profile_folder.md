---
title: "Thunderbird profile folder"
date: 2006-10-06
forum: Desktop Environments
---

### Post by keheikev on 2006-10-06
In linux I use tbird 1.5 as my newsreader. I would like to find the profile folder but this is what I find from the terminal.
drwxr-xr-x 11 root root 4096 2006-04-26 19:42 firefox
drwxr-xr-x 10 root root 4096 2006-04-20 12:04 thunderbird
kevin@kevinscomputer:/opt$ cd thunderbird
kevin@kevinscomputer:/opt/thunderbird$ ls -l
total 15892
drwxr-xr-x 3 root root     4096 2006-04-20 12:04 chrome
drwxr-xr-x 3 root root     4096 2006-04-20 12:04 components
drwxr-xr-x 8 root root     4096 2006-10-06 16:46 defaults
-rw-r--r-- 1 root root       52 2006-04-20 11:18 dependentlibs.list
drwxr-xr-x 4 root root     4096 2006-04-20 12:01 extensions
drwxr-xr-x 2 root root     4096 2006-04-20 11:45 greprefs
drwxr-xr-x 2 root root     4096 2006-04-20 12:01 icons
drwxr-xr-x 2 root root     4096 2006-04-20 12:01 init.d
-rwxr-xr-x 1 root root   174036 2006-04-20 12:03 libldap50.so
-rwxr-xr-x 1 
Here is what the directions say to do from mozilla to create a user.js file in the default directory > On Linux, the path is usually ~/.thunderbird/xxxxxxxx.default
and then add this
 > Don't abbreviate newsgroup names:
user_pref("mail.server.default.abbreviate", false);xxxx.default/
I find defaults but no xxxxxx.defaults profile folder.
TIA
Kiheikev

---

### Post by CatKiller on 2006-10-06
~ means your Home folder. Files that start with . are hidden. The directions are mostly correct - my profile is in ~/.mozilla-thunderbird.

---

### Post by Robbyx on 2006-11-29
I can not find either my thunderbird or Firefox profile folders. I looked in places-computer-filesystem. I made sure that show hidden files was ticked.

Where are those profiles?

---

