---
title: "just want File search (Should be easy!)"
date: 2008-01-07
forum: Desktop Environments
---

### Post by n2stc on 2008-01-07
Hi Gang,  I would just like to do a recursive search, starting at the top, showing all the files which end in .doc for example.  GNOME always yields 0 results.  I can't find the filter syntax in man ls or locate.  Thanks,

Stan:confused:

---

### Post by chandru.in on 2008-01-07
Use this command,

> find /<top_dir> -iname *.doc

---

### Post by beren.olvar on 2008-01-07
use:
find /dirname/ -iname *.doc
or try using tracker

cheers

---

### Post by NilsE on 2008-01-07
Or if you want it in a gui use the "Search for Files" under Places. It actually works pretty good once you get the options set.

The key is to select the search path at the highest level you want to start at like File System for all devices..

Then in the "Available option" turn on the ones you want like show hidden files and backups, etc.

Remember, that each time you use it you need to click on the Available option pull down button  to activate them again. Even though they stay set you have to open the window.

---

### Post by n2stc on 2008-01-07
Beautiful.  Thanks to all.  Any Idea why Gnome's file browser won't work?

---

### Post by chandru.in on 2008-01-07
It filters only current directory.

---

### Post by mcduck on 2008-01-08
'locate' is even better command-line search than 'find', as it uses a database which makes it very fast. Of course this also means that it doesn't find files you have added to your system very recently as it hasn't indexed them yet.

Many people are having problems with Tracker, the search tool used in Gnome. It seems to sometimes work perfectly and sometimes just do nothing. You can replace it with Beagle if you want, it's a bit more reliable but honestly never really worked for me.. The real problem is that as long as either one is installed, the normal search in Nautilus doesn't work as it tries to use Tracker/Beagle instead..

---

### Post by dbera on 2008-01-08
If you just want to search by name, then tracker/beagle are overkill. Use find or locate. The syntax for find takes a bit of practice to get used to but its worth it.

---

### Post by vanadium on 2008-01-08
The current find option within Nautilus uses tracker, and I feel indeed that is terribly misplaced. You cannot simply list a number of files that exist within a directory tree anymore within nautilus. Indeed, you still have Places - Search for files, but then you first have to indicate your starting search directory, so it is definitely less convenient than having that functionality within nautilus.

---

