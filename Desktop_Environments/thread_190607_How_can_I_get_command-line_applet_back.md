---
title: "How can I get command-line applet back?"
date: 2006-06-06
forum: Desktop Environments
---

### Post by tpratt on 2006-06-06
I used the regex functionality of the tool extensively.  It looks like I'd have to learn python and the deskbar API to do this with deskbar.  How can I get back my beloved command-line applet?

--tpratt

---

### Post by tonyr on 2006-06-06
Is ALT-F2 what you are looking for?  
System->Preferences->Keyboard Shortcuts->**Show the panel run application dialog**

---

### Post by tpratt on 2006-06-06
Unfortunately, no.  The command-line applet was a text-box/droplist you could put on a panel and create aliases based on regex's such as:

when:
^myalias *(.*)$

execute:
rdesktop -f -rdisk:xyz=/junk \1

It was very handy.

---

