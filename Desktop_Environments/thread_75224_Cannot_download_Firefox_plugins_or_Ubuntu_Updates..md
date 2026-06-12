---
title: "Cannot download Firefox plugins or Ubuntu Updates..."
date: 2005-10-13
forum: Desktop Environments
---

### Post by sardopsycho on 2005-10-13
Flash Player will not install into Firefox - it just says "failed", and the manual install does not work either.  Also, my automatic updates tells me "Unable to get exclusive lock - This ususally means that another package managment application (like apt-get or aptitude) already running.  Please close that application first"

I know I don't have these running...or at least I think I don't....what is going on??

PAul

---

### Post by drogoh on 2005-10-13
Also check for instances of Synaptic.  Also, open up the task list and look for instances of apt, apt-get, aptitude, etc.

---

### Post by kassetra on 2005-10-13
[QUOTE=sardopsycho]Flash Player will not install into Firefox - it just says "failed", and the manual install does not work either.  Also, my automatic updates tells me "Unable to get exclusive lock - This ususally means that another package managment application (like apt-get or aptitude) already running.  Please close that application first"

I know I don't have these running...or at least I think I don't....what is going on??

PAul[/QUOTE]

Sounds like you were trying to install flash in Synaptic and when it failed - it didn't release the lock file - which now would prevent you from using Synaptic.

There are a number of different ways to release the lock file - and if you're comfortable with the terminal, I will tell you how.

The least painful non-terminal way to release the lock file is to reboot the machine (all lock files are removed this way - because you're no longer using the processes.)

---

### Post by seshomaru samma on 2005-11-01
[QUOTE=kassetra]Sounds like you were trying to install flash in Synaptic and when it failed - it didn't release the lock file - which now would prevent you from using Synaptic.

There are a number of different ways to release the lock file - and if you're comfortable with the terminal, I will tell you how.

The least painful non-terminal way to release the lock file is to reboot the machine (all lock files are removed this way - because you're no longer using the processes.)[/QUOTE]

can you tell me how to release the lock file with the terminal?

---

