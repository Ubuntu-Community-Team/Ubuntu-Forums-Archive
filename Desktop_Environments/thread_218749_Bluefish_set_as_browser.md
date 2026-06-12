---
title: "Bluefish set as browser"
date: 2006-07-19
forum: Desktop Environments
---

### Post by arcejorge on 2006-07-19
Hi, it's the first time i post a problem, so i post in general support, there is a weird thing happening since i installed bluefish editor, every time i open a link from an application like kopete or gaim, it doesnt open firefox, it launches bluefish, downloads the file and opens it for editing, i really don't know how i can take it back to firefox.

i tried the preferred applications app in system menu, and selected firefox, but nothing happened..

Thanx in advance

---

### Post by orb9220 on 2006-07-19
run gconf-editor 
and look in desktop>applications>browser 
and see if the exec is set for firefox.

---

### Post by arcejorge on 2006-07-19
Hi,thanks for the reply i did that, and exec is set for firefox, also in the url-handlers section there is for http gnome-www-browser %s and if i run gnome-www-browser & in terminal, it opens firefox.

but it keeps opening bluefish from kopete

---

### Post by arcejorge on 2006-07-19
I solved it, it was because i installed kopete. a kde app in gnome and there was no konkeror, so it launched bluefish, so i installed konkeror and updated the file asociations, now it opens firefox


THANX:-D

---

