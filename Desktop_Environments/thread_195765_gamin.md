---
title: "gamin"
date: 2006-06-13
forum: Desktop Environments
---

### Post by garba on 2006-06-13
anybody knows what this cursed daemon is supposed to do? it doesn't come with man pages and it eats up lots of cpu cycles, what's worse, the whole distro seems to depend on it... tried googling for it but all i got is a bunch of complains from other users about the very same reasons I've just mentioned. Any clue?

---

### Post by rbalfour on 2006-06-13
Gamin is a file and directory monitoring system defined to be a subset of the FAM (File Alteration Monitor) system. This is a service provided by a library which allows to detect when a file or a directory has been modified.

Must be a different google then what I am using. ;)

[http://www.google.com/search?hl=en&q=gamin&btnG=Google+Search](http://www.google.com/search?hl=en&q=gamin&btnG=Google+Search)

first hit on the list.

---

### Post by WorLord on 2006-06-13
Technically, Gamin is everything rbalfour said it was.

Personally, Gamin is a hunk of junk that I'm glad was removed from Dapper (at least, the default Ubuntu has it removed, as GNOME and VFS talk directly to iNotify now - I hear tell that Kubuntu still uses it, which is a damn shame).

Anyway - what it does, realistically (besides eat clock cycles and suck up RAM) is allow file managers to dynamically update the contents of their folders as you view them.  With it, you can add or delete a file from the command prompt (or other means) and the changes will show up in your file manager if you're viewing that folder.  Without it, you'll have to manually hit "refresh".  

The deprication of Gamin is one of the reasons I moved to Dapper way early (month 2 of development).  I had to set up a script in Breezy to kill gam_server every hour or so (it would restart itself) becase of the memory leaks.

---

