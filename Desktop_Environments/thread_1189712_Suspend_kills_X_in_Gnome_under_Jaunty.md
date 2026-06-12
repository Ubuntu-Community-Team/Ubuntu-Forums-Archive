---
title: "Suspend kills X in Gnome under Jaunty"
date: 2009-06-17
forum: Desktop Environments
---

### Post by manfredlotz on 2009-06-17
Suspend / resume works fine I thought. However, after resuming all open applications are gone. 

Doing a second test and checking out the PIDs I saw that X and gnome were newly started.


Any idea, how I can track it down?


-- 
Manfred

---

### Post by manfredlotz on 2009-06-17
Hi all,
Should mention that I use "AccelMethod" "uxa" and after adding 
    Option        "EXAOptimizeMigration"        "true"
    Option        "MigrationHeuristic"        "greedy"

to device section of xorg.conf for the first time I could successfully resume. No X kill anymore.


Hope, this is a persistent behavior.


-- 
Manfred

---

### Post by manfredlotz on 2009-06-20
Didn't help. Was wishful thinking.

Sigh!

---

