---
title: "same users on the linux systems"
date: 2005-02-24
forum: Desktop Environments
---

### Post by gasparov on 2005-02-24
Hi,
    I don't know if this is the right place, this is more a general linux question...
I'm running Ubuntu in my room computer,on this system my user/group is gas, both with ID 1001. My p2p/ftp machine is running Mandrake 10.1 with same user/group name but this time with ID 501.This difference in ID it's a little problem, every file that is downloaded on mandrake got 644 or 664 as permission and owner is gas (501), that is my gas Ubuntu user (ID 1001) has no exec/write permission I need. I was thinking about setting up a common group between the two systems but wat happend with files that got 644 permissions? What would happend If i change my ID here in Ubuntu?

I didn't think when setting up groups/users during this installation and now I suppose is getting a mess to manage the fact.....

Thx

---

### Post by sebdah on 2005-02-24
I think it would be easiest to create a new group called p2p (for exampel) on both computers and give p2p the same ID. In Ubuntu you are able to set the new group ID. I suppose you are able to do the same in Mandrake, if not you can make it in terminal.

---

### Post by gasparov on 2005-02-25
[QUOTE=sebdah]I think it would be easiest to create a new group called p2p (for exampel) on both computers and give p2p the same ID. In Ubuntu you are able to set the new group ID. I suppose you are able to do the same in Mandrake, if not you can make it in terminal.[/QUOTE]
 Thx
Done by adding group p2p  with same ID as my ID on mandrake systems, averything seems working.....

---

