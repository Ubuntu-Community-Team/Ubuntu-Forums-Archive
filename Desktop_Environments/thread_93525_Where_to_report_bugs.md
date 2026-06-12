---
title: "Where to report bugs"
date: 2005-11-22
forum: Desktop Environments
---

### Post by steve_mcgarrett on 2005-11-22
I wrote a short list about bugs in ubuntu 5.10 out of my head:
1. new starters in Gnome-panel are always on the left after restarting Gnome
2. Mounted CDs and USB-sticks are displayed on top of desktop symbols
3. Icons of new files on desktop (e.g. from downloads) are not aligned to grid
4. After burning an audio CD with Gnome the CD is ejected and the windows still displays "fixiating"
5. You cannot delete a cd-rw with Gnome without burning to it afterwards
6. Gnome help is outdated and not translated to German
7. Evolution not completely translated to German
8. Checkbox "server needs authentification" doesn't stay checked
9. Wrong font names in new version of "fontconfig"
10. DVD-RAM is not burned with nominal speed
11. OpenGL graphics are corrupted
12. When typing I get messages about unknown keys
13. I cannot mount floppy discs
14. ...

Where do I report theese bugs to? To the Ubuntu team or to the project itself or both?

And what do you think about those bugs (rember: typed out of my head)?

---

### Post by 23meg on 2005-11-22
Even though some of yours aren't really reportable bugs, the place to go is [https://bugzilla.ubuntu.com/](https://bugzilla.ubuntu.com/) for general OS bugs and [https://launchpad.net/malone](https://launchpad.net/malone) for apps in Universe.

It helps to do a search in the forums and the wiki to see if the dysfunction you observe is observer by others (and possibly fixed) as well.

---

### Post by steve_mcgarrett on 2005-11-22
[QUOTE=23meg]Even though some of yours aren't really reportable bugs, the place to go is [https://bugzilla.ubuntu.com/](https://bugzilla.ubuntu.com/) for general OS bugs and [https://launchpad.net/malone](https://launchpad.net/malone) for apps in Universe.

It helps to do a search in the forums and the wiki to see if the dysfunction you observe is observer by others (and possibly fixed) as well.[/QUOTE]

I have a problem with understanding. If I report a bug e.g. in Evolution to the Ubuntu team how does the Evolution development team at Ximian or whereever know about the bug?

Or do the Ubuntu developpers report the bugs to the projects they belong to?

Or is it even the case that every distribution fixes bugs in software on their own (can't imagine that as several distributions would fix the same bugs again and again whereas the original sources from the project would stay buggy).

And which ones aren't reportable bugs?

---

### Post by 23meg on 2005-11-22
[Malone]("http://www.launchpad.net/malone") is an invaluable tool developed by Canonical to aid in this department. Whenever you report a bug with your Ubuntu-shipped Evolution and it's fixed, the patch is sent "upstream" (to the developers) and to all distros who ship Evolution, so that they can fix it as well. Most other distros have their own systems that do this but I have yet to see one that's as effective and practical as Malone.

---

### Post by earobinson on 2005-11-22
yup they are just that smart! :)

---

### Post by 23meg on 2005-11-22
> 1. new starters in Gnome-panel are always on the left after restarting GnomeDoes locking them fix this?
> 6. Gnome help is outdated and not translated to German
7. Evolution not completely translated to GermanBetter report this to the Gnome bugzilla if it already isn't.
> 11. OpenGL graphics are corruptedHow exactly? Most likely a video card driver problem; if the driver isn't the one that ships with Ubuntu it's out of scope
> 12. When typing I get messages about unknown keysProbably an X keyboard problem; search the forums and the wiki and post a problem thread if you can't find a solution.
> 13. I cannot mount floppy discsThis often comes up on the forum. Do a search and you'll most likely solve it.

---

### Post by steve_mcgarrett on 2005-11-22
> **23meg]Does locking them fix this?[/QUOTE]
Have to try it but locking would only be a workaround.

[QUOTE=23meg]How exactly? Most likely a video card driver problem said:**
> 
They appear "wrong" in the lower half of the screen
The driver is the mga driver coming with X.org

[QUOTE=23meg]Probably an X keyboard problem; search the forums and the wiki and post a problem thread if you can't find a solution.
The programmer of the kernel keyboard driver has listed it as a symptom and he obviously doesn't want to fix it.

[QUOTE=23meg]This often comes up on the forum. Do a search and you'll most likely solve it.[/QUOTE]
Yes I have read about the workaround but the simplest solution would be an updated pmount package in the update repository. But this won't be the case so I downloaded pmoung from the unstable release to "fix" it. Not a good solution.

---

