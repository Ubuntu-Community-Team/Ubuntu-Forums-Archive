---
title: "Customize bash autocompletion"
date: 2009-01-12
forum: General Help
---

### Post by mooseydoom on 2009-01-12
I'm looking for a way to customize bash autocompletion.  Is there a way to automatically switch between the "complete" and "menu-complete" modes so that if there is only a few matches, use the menu-complete mode, but if there is a large number of matches, use the complete mode?  (modes described in "man readline").  

Example:  Say there are two files, "apple" and "acorn".  Typing "a[tab]" would fill in "acorn".  Pressing tab again would fill in "apple".  If there are a bunch of files, "file1", "file2", "file3" ... "file100", Typing "file[tab]" would display all the possible completions instead of filling in "file1" because there are too many possible matches.

---

