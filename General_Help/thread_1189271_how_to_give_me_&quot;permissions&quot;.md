---
title: "how to give me &quot;permissions&quot;"
date: 2009-06-16
forum: General Help
---

### Post by xZachtmx on 2009-06-16
ok im trying to set something up through the terminal but i get an error when it tries to create a file its restricted:

error: could not create '/usr/local/lib/python2.6/dist-packages/msnp': Permission denied

how can i enable these permissions?

---

### Post by ZackM on 2009-06-16
sudo then the commands.

---

### Post by xZachtmx on 2009-06-16
you would think i know that by now... lol thanks!

---

### Post by Tyke91 on 2009-06-16
For more clarification, every file has a permissions string that contains 3 digits
let's call this file foo.txt

there are 2 (command line) ways you can affect the permissions of foo.txt
chown
and
chmod

chown changes the owner of a file. you can use it like this
```
chown user:usergroup foo.txt
```
where user is the new owner of the file and usergroup is the group that has access to the file.

chown usually has to be run with root privileges, so don't forget sudo in front.

chmod is not hard to understand, but the number system needs to be learned.

chmod can be used to give read, write and executable permissions to a file.
exectutable = 1
write = 2
read = 4

for the three digit number ###, the first digit is for the owner, the second is for the group and the third is for everybody else.


so foo.txt is now owned by user and usergroup, but we want to set specifics. let's say we want full access for the user, read access for the group, and nothing for anyone else. the 3 digit number is a sum of the permissions for each set of people.
so, 7 (exec+read+write) for the user, 4 (read) for the group, and 0 for everyone else would be done like this
```
chmod 740 foo.txt
```

one last thing. directories need to have executable permissions for somebody to browse through them. so if you want someone to have read only access to a directory, you need to give them a 5.

---

