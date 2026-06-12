---
title: "Get duplicate files with ~ extention?"
date: 2009-01-25
forum: General Help
---

### Post by Auraomega on 2009-01-25
Hi all,

I keep switching between my Vista PC and my Ubuntu laptop to code and every time I move my flash card between every file I've opened on my laptop ends up getting duplicated and having an ~ concatenated to the end of its extention. For example I get main.cpp on my PC, and main.cpp on my laptop, when I move back to my PC I get main.cpp and main.cpp~.

I'm assuming its something to do with mounting and unmounting the drive but I can't work out why or what to do to stop it.

-Aura

---

### Post by dcstar on 2009-01-25
> **Auraomega said:**
> Hi all,

I keep switching between my Vista PC and my Ubuntu laptop to code and every time I move my flash card between every file I've opened on my laptop ends up getting duplicated and having an ~ concatenated to the end of its extention. For example I get main.cpp on my PC, and main.cpp on my laptop, when I move back to my PC I get main.cpp and main.cpp~.

I'm assuming its something to do with mounting and unmounting the drive but I can't work out why or what to do to stop it.

-Aura

Nothing to do with it at all, all edited files have the previous version kept with a "~" appended (for safety) but these are hidden in Linux.

---

### Post by Auraomega on 2009-01-25
Oh ok, I just assumed because I only see them on a flash drive. Is there any way to turn this off as its mighty annoying?

-Aura

---

### Post by dcstar on 2009-01-25
> **Auraomega said:**
> Oh ok, I just assumed because I only see them on a flash drive. Is there any way to turn this off as its mighty annoying?

-Aura

Having a backup of source code annoying?!?, anyway go into whatever you are editing with and see if it has that option.

---

### Post by Auraomega on 2009-01-26
Yeah, I take regular backups myself on a different medium, backups in the same folder bug me as it makes it seem cluttered.

Anyway I'll take a look and see if theres any options, thanks.

-Aura

---

### Post by cdtech on 2009-01-26
Hey Auraomega,
I know the problem with the duplicate file issue. I use this command to remove those pesky files. The print flag lets me see which files are being deleted. Just go to the top level of the directory and run this command:
```
find ./ -name '*~' -exec rm '{}' ';' -print
```
To set up "gedit" to not save a backup file (~), open gedit go to "Edit > Preferences > Editor" and select not to save a backup copy.....

Hope this helps ya......

---

