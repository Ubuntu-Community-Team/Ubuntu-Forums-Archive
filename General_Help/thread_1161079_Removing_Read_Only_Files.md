---
title: "Removing Read Only Files"
date: 2009-05-16
forum: General Help
---

### Post by cssutto on 2009-05-16
Ubuntu 8.04

Using rsync to backup to external hard drive.

External drive getting full of old header files.

sudo rm -rf returns the message that the files are read only and can not be removed.

Changed to sudo su with no success.

These files are now in a .Trash-1000 folder.

I am in the correct folder or directory because otherwise I would not be getting the unable to remove message.

I have tried  sudo chmod 777 .Trash-1000
 with no results.

How do I get rid of these headers?

CSSJR

---

### Post by wanchai on 2009-05-16
Strange. If you are root (sudo), you should be able to delete anything. The f option should disable all questions whether you really want to do that, the r option means "recursive", i.e. you can delete directories including their contents. Now I don't know whether the rm you are executing is an alias for a rm with some option that could make it more save. "which rm" would tell you that. If you're running rm -f it would just add
the f option to whatever is in the alias. If you want the pure rm with -rf and nothing else, you should run \rm -rf. Well, that's how it works in csh.

Another stupid thing: the file system on the external drive isn't mounted read-only by any chance?

---

