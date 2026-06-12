---
title: "Issue with powermanga"
date: 2008-12-09
forum: Gaming &amp; Leisure
---

### Post by ShirishAg75 on 2008-12-09
Hi all, 
  Powermanga has been having issues on 8.10 . 

```

$ powermanga
couldn't find/open config directory '/home/shirish/.tlkgames'
attempting to create it... ok
(!)tools.c/load_absolute_file() can't open file  /home/shirish/.tlkgames/powermanga.conf (No such file or directory)
(!)config_file.c/configfile_load() lisp_read_file(/home/shirish/.tlkgames/powermanga.conf) failed!
(!)menu_sections.c/high_scores_load_file() /var/games/powermanga/powermanga.hi file is empty!
(!)menu_sections.c/high_score_save() open (/var/games/powermanga/powermanga.hi) return: Permission denied


```

I see two issues here :-

a. It shouldn't need to give that, if there isn't a .conf file it should
make a .conf file in .tlkgames or preferebly in .config (as per free
desktop specification .

b. It be putting those scores in the .tlkgames directory and not in
/var/games/powermanga.hi

I have already made the bug as [lpbug]306305[/lpbug]

If anybody knows anything please reply on the bug itself.

---

