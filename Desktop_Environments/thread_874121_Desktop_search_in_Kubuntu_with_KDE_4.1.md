---
title: "Desktop search in Kubuntu with KDE 4.1"
date: 2008-07-29
forum: Desktop Environments
---

### Post by ponkarthik on 2008-07-29
Hi
  I have been using Google desktop search with KDE 3.5 in Kubuntu 8.04. But since moving over to kDE 4.1 I am not able to use it. The icon does not show up in systray and the gdialog also does not come up on pressing the hotkey (ctrl + ctrl). If I start gdlinux from CLI then it runs for a short time and I am able to access it from firefox after which it seems to crash.

Has anyone got it working ?

Alternatively I tried to get strigi working but it gives the error - 

'Unknown backend type: sopranobackend'

Any solutions for desktop search ?

Thanks
Karthik

---

### Post by vegetali on 2008-09-16
I have exactly the same problem. I used tracker with GNOME, but there is not search tool in KDE4: neither tracker nor strigi work. Any suggestion?

---

### Post by dualpretop on 2008-09-16
Dolphin...Tools...Find file

---

### Post by schnarkle on 2008-09-16
same problem here as well  :(

---

### Post by vegetali on 2008-09-17
thanks for the answer dualpretop
 but I guess you did not get the problem. While Kfind can search for file names (and maybe for contents in textual files), search tools like tracker or strigi are much more powerful. They first index your file; this indexing includes words in pdf, dvi, postscript etc files, and also tags in music, video and image files. Then, when you search a keyword, they instantly give you the results: in which file and where is the keyword located.

In particular, I have a huge (10Gb) professional library that I often use for reference. I just search the word I need and I can see immediately the appropriate reference book (that is, the right page in some pdf file), just using tracker. Unfortunately I do not know anything like this for KDE (strigi does not work), and Kfind is nowhere close. Kfind is just the good old file search we have since 1996 and in fact it is not even in the default kubuntu installation.

---

### Post by schnarkle on 2008-09-17
I found a search tool called Recoll.[http://www.lesbonscomptes.com/recoll/]("http://www.lesbonscomptes.com/recoll/")

so far it is indexing and searching well for me...

---

### Post by vegetali on 2008-09-18
thanks, I ll give it a try

---

### Post by mqp on 2008-11-01
I had also problems with google desktop. Now it appears to work in following way:

stop the process: $killall gdl_service
take out the system tray widget
reload: gdlinux start &
reput the system tray as widget

This has worked for me, although I still don't know how to make it happen "automatically" (how to make kde load first google desktop and then the system tray...)
Hope this helps,
mqp

---

### Post by archie_paulson on 2009-02-05
I've also been hoping for a decent kde4 desktop search tool.  But until one arrives, beagle (the Gnome tool) has worked well for me.

---

