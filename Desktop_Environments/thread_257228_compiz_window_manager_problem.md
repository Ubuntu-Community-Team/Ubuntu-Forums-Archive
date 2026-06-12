---
title: "compiz window manager problem"
date: 2006-09-14
forum: Desktop Environments
---

### Post by ruya on 2006-09-14
Hi,

I had xgl and compiz working fine but when came back from vacations I updated ubuntu (automatic update) and then made apt-get dist-upgrade to update the compiz packages. Now I don't have the windows borders and the keyboard shortcuts don't work. When I try to open the Window Preferences window I get an error message saying that the window manager is not registered.

Thank you

---

### Post by neoeden on 2006-09-14
Bump for great justice (and an answer).

---

### Post by PathSpace on 2006-09-14
Is everyone who has updated Compiz having this problem?

I might not update if that is the case.

---

### Post by frequenicity on 2006-09-14
see if:

nohup cgwd --replace

works.

---

### Post by ruya on 2006-09-14
It doesn't work. There is something buggy with the d-bus.
The error message I get when trying to open the window preferences is - window manager 'unknown' has not registered a configuration tool.
It happens with my gnome session too ( without Xgl).

---

### Post by turbojugend_gr on 2006-09-14
It is thouroughly discussed in theese threads, that's where I found a solution for it too: 1.[http://www.ubuntuforums.org/showthread.php?t=250489&highlight=todays+compiz+updates](http://www.ubuntuforums.org/showthread.php?t=250489&highlight=todays+compiz+updates)

2.[http://www.ubuntuforums.org/showthread.php?t=252796&highlight=todays+compiz+updates](http://www.ubuntuforums.org/showthread.php?t=252796&highlight=todays+compiz+updates)

---

### Post by frego on 2006-09-14
After taking today's compiz updates, I'm having the same issue, no title bars using compiz and metacity.  But running:
nohup cgwd --replace
brought them back for me.

---

### Post by DomaZ on 2006-09-14
I have very good news for you

check 5 and 15 posts at that address [http://www.compiz.net/topic-4375-tit...-with-ati-x800](http://www.compiz.net/topic-4375-tit...-with-ati-x800)


Good luck

---

