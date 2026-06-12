---
title: "Creating a local shared directory..."
date: 2006-01-10
forum: Desktop Environments
---

### Post by encompass on 2006-01-10
I would like to have a folder that is fully accessable from users in a certain group... do I just create a directory and give it the groupd and user ownership of blabla... or is there a better way?

---

### Post by Ampersand on 2006-01-10
You could create the directory, then right-click on it in nautilus, go to Properties and then the Permissions tab. You can then select the group you want to be able to access it, and select read, write and execute for the group members.

You can also use the command line:

```

mkdir /directory
chgrp -R group /directory
chmod -R 774 /directory

```
-R sets the properties recursively, 774 sets it to read, write and execute for owner and group; and read for others. See the man pages for the commands for more details, or run them with --help.

---

### Post by encompass on 2006-01-23
cool thanks... so I can create a group and bind anyone I want to that group... then create a dir and make it part of that group?

---

### Post by Tichondrius on 2006-01-23
correct

---

