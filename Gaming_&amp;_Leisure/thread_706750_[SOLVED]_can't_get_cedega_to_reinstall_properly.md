---
title: "[SOLVED] can't get cedega to reinstall properly"
date: 2008-02-24
forum: Gaming &amp; Leisure
---

### Post by noremacyug on 2008-02-24
[COLOR="Red"][SIZE="3"]mod please delete/close, started new thread regarding the issue.[/SIZE][/COLOR]

i had cedega installed earlier and then uninstalled it.  now when i go to reinstall it doesn't not install correctly.  i've tried uninstalling it from the synaptics manager, as well as using

```
sudo aptitude purge cedega
```
also purged cedega small and transgaming

after this i tried reinstalling and it just isn't working.  files get placed in the files system, but i don't get the shortcuts added to applications, nor does it install the engine.

how can i wipe out any trace of cedega completely?[COLOR="Red"][/COLOR]

---

### Post by em3raldxiii on 2008-02-24
Not sure if this will help, but try this one:

```
sudo aptitude install -f
```

after you've uninstalled/purged everything.

---

### Post by noremacyug on 2008-02-24
> **em3raldxiii said:**
> Not sure if this will help, but try this one:

```
sudo aptitude install -f
```

after you've uninstalled/purged everything.
did that, i assume i attempt to reinstall cedega now?

also if you don't mind, what is the aptitude command as well as what does the command line that you gave me do?  i'm trying to learn rather than just go through the motions.

much appreciated!

(edit) - tried this and then reinstalled.  still no go.

---

### Post by noremacyug on 2008-02-24
mod, please close/delete this thread.

thanks

---

### Post by em3raldxiii on 2008-02-25
aptitude is almost exactly the same as apt-get, except that it handles dependencies (especially when uninstalling) better than apt-get.

The specific line I gave you checks the stuff you have installed and sees if anything is partially done, or if there are missing dependencies, then it offers choices (under some circumstances) as to what you would like to do to fix the problem.  Often it will ask if you want to re-install a specific package, or if you would like to remove un-needed dependencies, etc.

Out of curiosity, why do you want this thread closed?

---

### Post by noremacyug on 2008-02-25
> **em3raldxiii said:**
> aptitude is almost exactly the same as apt-get, except that it handles dependencies (especially when uninstalling) better than apt-get.

The specific line I gave you checks the stuff you have installed and sees if anything is partially done, or if there are missing dependencies, then it offers choices (under some circumstances) as to what you would like to do to fix the problem.  Often it will ask if you want to re-install a specific package, or if you would like to remove un-needed dependencies, etc.

Out of curiosity, why do you want this thread closed?

appreciate it man.

i ended up starting another thread regarding this issue, but in a more vague manner.  just wanted to know how to completely remove any program.  i ended up getting it sorted out and am good to go now.  here's the new thread  [http://ubuntuforums.org/showthread.php?t=706959](http://ubuntuforums.org/showthread.php?t=706959)

---

### Post by em3raldxiii on 2008-02-26
Fantastic :D  Thanks for the link.  It's great to have it cross-referenced too, in case someone else has the same issue.  Cheers!!

---

### Post by Crafty Kisses on 2008-02-26
I guess you can mark the thread solved. :KS

---

### Post by noremacyug on 2008-02-26
> **Codename said:**
> I guess you can mark the thread solved. :KS


i suppose so. sorry, still a newb to both this forum and linux.:)

---

