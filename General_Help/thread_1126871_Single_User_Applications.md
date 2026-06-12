---
title: "Single User Applications"
date: 2009-04-15
forum: General Help
---

### Post by Joeb454 on 2009-04-15
Ok, quick question (I hope!)

I'm installing a multi-user system, which is a first for me, as I've never had to do so in the past.

What I want to know, is how I would go about installing an application, but then allowing only 1 user to actually run it.

Lets say I have Mary Bob & Bill on my system. Bill installs application x.

I now want the only user to be able to ever run that app to be Bill. I just have no idea how I'd go about getting that to work.

I tried chowning the file to bill:bill, but that didn't work :(

Any help would be greatly appreciated :)

---

### Post by 3Miro on 2009-04-15
Every file has owner and group and then permissions for those. If you type "ls -l" in the terminal you will see something like:
```

drwxr-xr-x 14 me me   4096 2009-04-15 20:03 Documents

```

Basically d stands for directory (folder) then you have the three sets of permissions (owner, group, everyone else).

r - is read
w - is write (modify)
x - is execute (start as a program) or in the case of a folder, it means enter.

Above means that the owner (me) of Documents can enter the directory and modify it. Members of the group (me) can only enter, but cannot rename/delete the folder. Everyone else has the same permissions as the group people.

You set permissions with chmod:
```

chmod 700 myPersonalProgram
chmod 600 myPersonalDocument
chmod 755 mySharedProgram
chmod 644 mySharedDocument

```
700 means that only I can touch this file and I can also execute it (use it only for programs/scripts). 600 means only I can read this file (use it for private documents). 755 means that anyone can run this program, however, only I can change it. 644 means anyone can read this file, but only I can change it.

Note that no matter what, root can always modify permissions on files (or someone with sudo command). Make sure you are the only person with superuser privileges.

---

### Post by ostrm on 2009-04-15
Hi!

One solution might be:
Create different groups, chgrp and chmod the executing permissions of those binaries you want to restrict access to. Make then users selectively members of the group.

But in the end this might be a pain if you'd like to grant different groups access to different overlapping subsets of executables.

The *far* superior solution is to create chroots or "jails" on a per user basis (e.g. in *every single* home directory). You should have a look at **[jailkit](http://olivier.sessink.nl/jailkit/)** which helps nicely in building jails.

ostrm

---

### Post by Joeb454 on 2009-04-15
Awesome :) Thanks a lot.

I should really look into permissions in a bit more detail ;) I did also think of groups, as then you can add a user to the group, which would likely work just as well, if not better :)

---

### Post by bodhi.zazen on 2009-04-15
Go with permissions first.

chown root.bill foo
chmod o-x foo

If you have more then a few users , go with acl

---

