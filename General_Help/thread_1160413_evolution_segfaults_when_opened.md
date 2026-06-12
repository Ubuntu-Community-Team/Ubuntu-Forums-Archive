---
title: "evolution segfaults when opened"
date: 2009-05-15
forum: General Help
---

### Post by Kevin Fischer on 2009-05-15
I've been using evolution for some time without any issues.  

However, a couple of days ago I noticed some strange behavior (message previews were occasionally for the wrong message), and now evolution crashes whenever I try to start it (even after a system restart).

Here's the output when I run it in terminal:

```
** (evolution:2078): DEBUG: mailto URL command: evolution %s
** (evolution:2078): DEBUG: mailto URL program: evolution

(evolution:2078): camel-WARNING **: something went wrong terribly during db creation 


(evolution:2078): evolution-mail-WARNING **: Could not setup local store/folder: unable to open database file

(evolution:2078): camel-CRITICAL **: camel_object_is: assertion `o != NULL' failed

(evolution:2078): camel-CRITICAL **: camel_object_ref: assertion `CAMEL_IS_OBJECT(o)' failed

(evolution:2078): camel-WARNING **: something went wrong terribly during db creation 


(evolution:2078): evolution-mail-WARNING **: Could not setup local store/folder: unable to open database file
Segmentation fault

```


Any ideas on what I should do to be able to use evolution again?

---

### Post by dcstar on 2009-05-15
> **Kevin Fischer said:**
> I've been using evolution for some time without any issues.  

However, a couple of days ago I noticed some strange behavior (message previews were occasionally for the wrong message), and now evolution crashes whenever I try to start it (even after a system restart).

Here's the output when I run it in terminal:

```
** (evolution:2078): DEBUG: mailto URL command: evolution %s
** (evolution:2078): DEBUG: mailto URL program: evolution

(evolution:2078): camel-WARNING **: something went wrong terribly during db creation 


(evolution:2078): evolution-mail-WARNING **: Could not setup local store/folder: unable to open database file

(evolution:2078): camel-CRITICAL **: camel_object_is: assertion `o != NULL' failed

(evolution:2078): camel-CRITICAL **: camel_object_ref: assertion `CAMEL_IS_OBJECT(o)' failed

(evolution:2078): camel-WARNING **: something went wrong terribly during db creation 


(evolution:2078): evolution-mail-WARNING **: Could not setup local store/folder: unable to open database file
Segmentation fault

```


Any ideas on what I should do to be able to use evolution again?

Firstly rename your (hidden) .evolution folder so a new one is created when you start Evolution.

If it does start ok then something is corrupted in the old folder, but you can then copy stuff from the old to the new one at a time until you find what is broken.

---

