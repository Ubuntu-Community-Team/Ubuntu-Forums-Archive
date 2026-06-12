---
title: "file manager not showing any files"
date: 2005-12-12
forum: Desktop Environments
---

### Post by linuxgrrl on 2005-12-12
I think I've borked something ... whenever Konqueror is in "file manager" mode it shows no files (even though I *know* I have files with my permissions on them).  If I switch to "simple browser" mode they are there.

I've tried playing around with the "filter" option for "file manager view" to see if that was the problem, but I can't seem to find a "cancel all filters" option, nor even bring up a dialog box relating to filters.  

Any ideas?  I can't reset all of KDE ... it took me forever to get the colors and fonts readable on my TV and I'm not sure I could replicate it what I did.
thanks,
Mary

---

### Post by mlomker on 2005-12-12
You could try deleting this preferences file:

```

rm ~/.kde/share/apps/konqueror/profiles/filemanagement

```

---

### Post by linuxgrrl on 2005-12-13
[QUOTE=mlomker]You could try deleting this preferences file:

```

rm ~/.kde/share/apps/konqueror/profiles/filemanagement

```[/QUOTE]

thanks much, I'll try it tonight and see what happens!

---

### Post by linuxgrrl on 2005-12-16
hey, it worked. awesome, thanks.

---

