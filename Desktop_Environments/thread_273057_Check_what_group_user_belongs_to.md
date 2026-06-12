---
title: "Check what group user belongs to?"
date: 2006-10-07
forum: Desktop Environments
---

### Post by iluminate on 2006-10-07
Hello all,

How on earth can I check what group a user belongs to via terminal?
And also, if the user is in the wrong group, how do I add the user to a new group?

Cheers!

---

### Post by iluminate on 2006-10-07
Think I found it -
```
groups [username]
```
Now if I want to add that user to groupname "wwwadmins" and the user is allready a member in another group - how is this done?

Cheers

Well sorry for posting but found how 2....I think.
If others have the same questions here you go.
How to check what group a user belongs to:
groups username
How to add the user to groups?
usermod -G group1,group2 username

Hope it is correct, if not then someone can reply with the correction :-D

---

### Post by taurus on 2006-10-07
```
id
``` also works too...

---

### Post by mihaisofti on 2006-10-12
If you use the -G option without -a option, any groups to which you are already a member will be removed.  You must append using -a.

All this information is in man usermod, groupmod, useradd, groupadd

---

### Post by mitch.c on 2006-10-12
> **iluminate said:**
> Think I found it -
```
groups [username]
```
Now if I want to add that user to groupname "wwwadmins" and the user is allready a member in another group - how is this done?

Cheers

Well sorry for posting but found how 2....I think.
If others have the same questions here you go.
How to check what group a user belongs to:
groups username
How to add the user to groups?
usermod -G group1,group2 username

Hope it is correct, if not then someone can reply with the correction :-D
Be careful! Using this command with an existing user...
```
usermod -G group1,group2 username
```
... will add username to group1 and group2, but REMOVE them from other groups they already members of!!!

From the usermod man page:
> If the user is currently a member of a group which is not listed, the user will be removed from the group. This behaviour can be changed via -a option, which appends user to the current supplementary group list.

Change to:
```
usermod -aG group1,group2 username
```
Or use:
```
adduser username group
```

---

