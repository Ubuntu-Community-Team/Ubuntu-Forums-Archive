---
title: "File system giant error"
date: 2009-04-09
forum: General Help
---

### Post by lachrymose on 2009-04-09
Hi guys, I have been really hesitant to make a post for a while, but its been bugging me for too long and I have come to hate my other Windows 7 partition.

This is about the third time I have had Ubuntu installed on my laptop. The first two times have been working great (after configured) with no problems. However, this time (8.04), when trying to compile some c++ in Kdevelop, I get this strange error: EDIT: It compiles fine, but I meant to say when launching through Kdevelop.

```
/bin/sh: /home/connor/Projects/Physics/physics/debug/./src/physics: not found
Press Enter to continue!

```

(physics being the name of my program. Also notice the "." as a folder name (which is not a folder)) Now another thing weird happened. I installed Dolphin, and when opening some folders, it says they aren't really any folders there. Thats when open My Documents, etc. Can someone please guide me in the right direction? Or should I just re-install. THANKS! :D

---

### Post by Vaphell on 2009-04-09
can't say what's the problem, but i think . is absolutely valid part of directory path - it means 'current dir' just like .. means 'parent dir'

/home/connor/Projects/Physics/physics/debug/./src/physics equals
/home/connor/Projects/Physics/physics/debug/src/physics

what do you get when you run
cd /home/connor/Projects/Physics/physics/debug/src/physics in terminal?

---

### Post by lavinog on 2009-04-09
> **lachrymose said:**
> 

```
/bin/sh: /home/connor/Projects/Physics/physics/debug/./src/physics: not found
Press Enter to continue!

```

(physics being the name of my program. Also notice the "." as a folder name (which is not a folder)) Now another thing weird happened. I installed Dolphin, and when opening some folders, it says they aren't really any folders there. Thats when open My Documents, etc. Can someone please guide me in the right direction? Or should I just re-install. THANKS! :D

the ./ folder is a reference to the current folder...it shouldn't make any difference
/folder/a/./b is the same as /folder/a/b

have you tried looking for the folder using the terminal?

Also why is this considered a giant error?
Edit: just noticed Vaphell already answered this. I need to refresh before replying ;)

---

### Post by lachrymose on 2009-04-09
> **Vaphell said:**
> 
what do you get when you run
cd /home/connor/Projects/Physics/physics/debug/src/physics in terminal?

No such file or directory. 
cd Projects/Physics/physics/debug/src however gets me somewhere.

I think of it as a big file system error because it seems to effect everything. When I go to Places > Documents, Dolphin (which I thought i uninstalled.. wierd) gives an error saying "The file or folder /home/connor/'file:/home/connor/Documents' does not exist

sooo weird and frustrating. I think I will just wait until 9.10 comes out and do a fresh install and cross my fingers it will fix.

---

### Post by soltanis on 2009-04-09
First of all, your user name IS connor, right, so your home directory is /home/connor?

Second, I don't see what the problem here is, you have a missing directory that seems to be reported by every program you are running as universally missing. Perhaps you accidentally moved this directory (I do that sometimes when I use the file manager and click wrong with the mouse)?

How are you so sure this directory exists, and that it is the filesystem's fault, not your own?

BTW not being accusing or anything, just need clarification.

---

