---
title: "Let's stop giving destructive advice"
date: 2009-02-23
forum: General Help
---

### Post by lykwydchykyn on 2009-02-23
Something I am noticing more and more on these forums, and that I'm guilty of myself, is that a lot of people give destructive troubleshooting advice.  What I mean is, you tell people to delete things that may be important in order to fix a problem.

Biggest offender I see is telling people to delete dotfiles when they have a program glitch, e.g. deleting ~/.mozilla when having firefox issues or ~/.openoffice.org when having OpenOffice issues.

It takes only a little more effort to tell people to rename these files/directories and accomplishes the same thing, with the benefit that if your brilliant advice DOESN'T fix the problem they haven't needlessly flushed their settings, bookmarks, extensions, etc.

Along the same lines, it takes only a little more effort to advise people to backup a config file before editing, or to comment out default settings before changing them (instead of changing the line directly).

These things have always been "best practice" for Unix/Linux administration, and for good reason; we should be promoting them when instructing new users.

---

### Post by eldragon on 2009-02-23
deleting is dumb.

what you ought to say is: 
```

mv .offending_settings_folder .offending_settings_folder.backup

```

thats what ive always suggest, never ever delete without certainty it will help

---

### Post by Zill on 2009-02-23
Good advice!  This should be in a "sticky" somewhere. :-)

---

