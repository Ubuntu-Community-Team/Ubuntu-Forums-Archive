---
title: "(avant-window-navigator) File icons in stacks applet"
date: 2009-01-17
forum: General Help
---

### Post by methadone on 2009-01-17
Hey everyone,

I've been trying to create shortcuts for my partitions and so I created a directory with 3 "script files" each to run a different "nautilus /path/" command. I've assigned icons to each of these files (via nautilus' file properties) and pointed AWN Stacks' Folder backend setting to the path where I had these scripts.
Now, they appear fine and function correctly when clicked, however their icons don't appear (they all have page icons (i.e. text files)).

Is there a way to make AWN Stacks load the files' assigned icons? Or maybe there is a way to assign these files icons via AWN itself?

Also, is there a way to change the Stack applet's icon? (the one that appears on the AWN bar itself)

Any thoughts?

---

### Post by t0n1 on 2009-05-11
Have you found a solution to this problem?

I've another annoyance: the stacks applet also shows two items which it shouldn't:
.gtk-bookmarks and .recently-used.xbel.
Should these not be hidden?

---

### Post by methadone on 2009-05-12
Hey tone,

Unfortunately, no. I've given up to be honest :)

Anyhow, regarding your problem; I can't say I have an answer but this is for sure a setting or a bug. Hidden files should not be showed.

Thanks for the reply ;p
-meth

---

### Post by moonbeam on 2009-05-12
> **methadone said:**
> Hey everyone,

I've been trying to create shortcuts for my partitions and so I created a directory with 3 "script files" each to run a different "nautilus /path/" command. I've assigned icons to each of these files (via nautilus' file properties) and pointed AWN Stacks' Folder backend setting to the path where I had these scripts.
Now, they appear fine and function correctly when clicked, however their icons don't appear (they all have page icons (i.e. text files)).

Is there a way to make AWN Stacks load the files' assigned icons? Or maybe there is a way to assign these files icons via AWN itself?

Also, is there a way to change the Stack applet's icon? (the one that appears on the AWN bar itself)

Any thoughts?


I don't use stacks myself... but I expect you just need to use desktop files that Exec the scripts (you can assign whatever icon you want in the desktop file).  Add the the desktop files to the stack instead of scripts.

Regarding changing the icons... most applet icons can be changed by drag and drop of the desired icon into the applet.  Not sure if this is enabled in stacks though (actually I suspect it probably is not).

There has definitely been some discussion about a complete rewrite of stacks for the 0.4 release.

---

