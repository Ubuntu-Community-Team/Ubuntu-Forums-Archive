---
title: "Timestamps not preserved"
date: 2008-05-23
forum: Desktop Environments
---

### Post by opg on 2008-05-23
Can't believe I am the only one having this problem, but I do not find any references to  it.  Ubuntu 8.04. Copying files by drag/drop changes the timestamp to the current time.  I have seen this mentioned as a Nautilus bug (and a very serious one, IMHO).  However, the same happens on the command line:
   cp oldfile newfile
sets the timestamp of newfile to the current time.
   cp -p oldfile newfile
preserves it.  But according to the manual this should be the default.  Maybe not a Nautilus bug after all?

---

### Post by jakon on 2008-05-25
This *is* a bug in nautilus, it is known already ( [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/215499](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/215499) ), people are working on fixing it.

---

### Post by tormod on 2008-06-11
Nautilus should not necessarily do exactly what "cp" without options do. cp has historical reasons for the way it works, and has to keep on doing exactly what it always did. OTOH nautilus has no way for the user to add any "-p" option... IMHO nautilus should do what's intuitive for its users, and what every other file manager on every OSe does. And what it did in the previous release...

This is definitely not only a bug, but a regression, since time stamps were preserved in Ubuntu 7.10.

Unfortunately the developers involved don't consider this bug as important as some of us others do. IMHO this should have been fixed before Ubuntu 8.04 was released. It was known to some people months in advance.

However, please do *not* vent your frustration in the bug reports. Bug reports are for technical discussions and providing the technical information needed to fix the bug the best way. There is already sufficient information and user comments.

This is more symptomatic of developer attitude and you can't really force them. Most of them are doing all this great work in their free time. However it should be the duty of a distribution meant for normal people/humans etc to get such things fixed promptly.

---

### Post by ajgreeny on 2008-06-12
You can always use another file manager as default if you wish, such as thunar or gnome-commander or (my favourite) xfe, all of which preserve timestamps.

---

