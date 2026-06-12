---
title: "Wine: Cannot find my xp apps"
date: 2005-12-27
forum: General Help
---

### Post by rasmusbp on 2005-12-27
Hi,


I'm trying to make wine run a program from my windows xp partition (FAT formatted - 32, I think).  Ubuntu automatically mounts it, and it's listed as "hda1" in the "places" menu. 

However, when I give the following command in a (root) concole, I get a "wine: cannot find [the .exe file]" error.

> wine /media/hda1/Program Files/Mindjet/Mindmanager 6/MindManager.exe

More specifically, I get this: 

> root@ubuntu:/home/rasmus# wine /media/hda1/Program Files/Mindjet/Mindmanager 6/MindManager.exe
Warning: Language 'en_DK' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_DK' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_DK' was not recognized, defaulting to 'en_US'.
wine: cannot find '/media/hda1/Program'
root@ubuntu:/home/rasmus#


In the [Wine Wiki]("http://www.winehq.org/site/docs/wine-faq/index#WINE-CANNOT-FIND-MS-WINDOWS-ON-MY-DRIVE"), under 6.2 (Q: I have installed and configured Wine, but Wine cannot find MS Windows on my drive. Where did I go wrong?), it says that:

> Remember too that unless your version of UNIX can see through it, or you are running a utility that can see through it, your DOS partition must not be located on a Drivespaced, Doublespaced or Stackered partition, as neither Linux, FreeBSD, NetBSD or Wine can natively 'see' files located in these compressed DOS partitions.

Check your path statements in the wine.conf file. No capital letters may be used in paths, as they are automatically converted to lowercase. 


I haven't a clue what that means... (newbie alert! don't get too technical on me...)

Can someone please help?

Cheers,

Rasmus
Copenhagen, Denmark

---

### Post by schilcha on 2005-12-28
[QUOTE=rasmusbp]
root@ubuntu:/home/rasmus# wine /media/hda1/Program Files/Mindjet/Mindmanager 6/MindManager.exe
Warning: Language 'en_DK' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_DK' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_DK' was not recognized, defaulting to 'en_US'.
wine: cannot find '/media/hda1/Program'
root@ubuntu:/home/rasmus#
[/QUOTE]

This error comes from spaces in filenames (frequently used in win and a pain in the ass in unix - not a problem though). Spaces are deliminators for command line arguments. So wine thinks there are 3 arguments passed (1. "/media/hda1/Program", 2. "Files/Mindjet/Mindmanager" and 3. "6/MindManager.exe") 

So, either prepend each space with a backslash ```
wine /media/hda1/Program\ Files/Mindjet/Mindmanager\ 6/MindManager.exe
``` or enclose the path-and-exe-file in quotes (single or double shouldn't matter in this case) ```
wine "/media/hda1/Program Files/Mindjet/Mindmanager 6/MindManager.exe"
```

Good Luck!

BTW, can't help you with actual wine-issues...

---

### Post by Alex1971 on 2007-09-27
> **schilcha said:**
> This error comes from spaces in filenames (frequently used in win and a pain in the *** in unix - not a problem though). Spaces are deliminators for command line arguments. So wine thinks there are 3 arguments passed (1. "/media/hda1/Program", 2. "Files/Mindjet/Mindmanager" and 3. "6/MindManager.exe") 

So, either prepend each space with a backslash ```
wine /media/hda1/Program\ Files/Mindjet/Mindmanager\ 6/MindManager.exe
``` or enclose the path-and-exe-file in quotes (single or double shouldn't matter in this case) ```
wine "/media/hda1/Program Files/Mindjet/Mindmanager 6/MindManager.exe"
```

Good Luck!

BTW, can't help you with actual wine-issues...

This fixed my problem!! thank you.

---

