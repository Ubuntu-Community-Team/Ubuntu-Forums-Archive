---
title: "Wget: updating a mirror"
date: 2008-12-30
forum: General Help
---

### Post by lucvdv on 2008-12-30
I'm trying to mirror a site ([http://www.gamingcommission.fgov.be](http://www.gamingcommission.fgov.be)) and update the mirror at regular intervals.

This is primarily meant to detect new and changed pages and files.  While at it, I intended to set it up as a local mirror to get the added benefit of that (the site has a tendency of going down a LOT).

I'm using wget 1.10.2 on Ubuntu Server 7.10, apparently they don't have 1.11.x in the repository yet (just scanned for and installed updates today to make sure).


The initial local copy works perfectly, it is fully browsable, etc.

Then when I run wget again with the exact same command line arguments, this is what happens:

1) It checks only the top page (index.html) and direct descendants.  If there are no changes there, it just stops.  In other words, it only detects a change in a page if the parent of that page in the link tree has also changed.

2) It messes up links in the pages it re-checks.  Any link to a page that isn't downloaded again (because it hasn't changed) is replaced by an absolute link to the original server, but using the filename of the local copy.

An example of an URL mutilated by (2):

Original:
[INDENT]jsp/main.jsp?lang=NL[/INDENT]
Mirror, initial copy:
[INDENT]jsp/main.jsp%3Flang=NL.html[/INDENT]
Mirror, after one update:
[INDENT]http://www.gamingcommission.fgov.be/jsp/main.jsp%3Flang=NL.html[/INDENT]


I am using these command line parameters:
[INDENT]--mirror
--html-extension
--convert-links
--backup-converted
-w 2
--random-wait
-p
--no-check-certificate
--read-timeout=60
-e robots=off[/INDENT]

Is there something wrong with my parameters?
Is it something in the site?
Is it a bug?  Fixed in 1.11.4?


BTW, in case someone wants to test it out locally: total size of the mirror is 116MB, but you can significantly reduce that by skipping the .pdf and .doc files.

---

