---
title: "I can't change my homepage on firefox"
date: 2009-05-13
forum: General Help
---

### Post by dragos240 on 2009-05-13
I open preferences, and I set it for keyboarder.com. I clicked home and there it was, keyboardr.com. When I closed firefox, and opened it again, the default homepage was there. I do this every day, it never works!

---

### Post by dragos240 on 2009-05-14
Bump

---

### Post by dragos240 on 2009-05-15
Bump.

---

### Post by Dr.Vista on 2009-05-15
> **dragos240 said:**
> Bump.
Another way of adding a page to your homepage is by dragging the favicon of the page to the home icon in Firefox.

---

### Post by dragos240 on 2009-05-15
I'll try it. Thanks for replying

It worked, till I closed firefox. Then I opened it, only to display the default canonical designed homepage.

---

### Post by dragos240 on 2009-05-15
Also I just opened firefox via gksu, I can save my homepage on root, but not this account.

---

### Post by Dr.Vista on 2009-05-15
> **dragos240 said:**
> Also I just opened firefox via gksu, I can save my homepage on root, but not this account.
That's pretty weird. Seems that your settings are being wiped out everytime you close firefox.

---

### Post by michy99 on 2009-05-15
Somewhere in ~/.mozilla/firefox/ is a file that saves all your preferences. It sounds like the permissions on that file is not set properly, so it cannot be saved. Unfortunately, I don't happen to know what file it is.

---

### Post by dcottingham on 2009-05-15
> **michy99 said:**
> Somewhere in ~/.mozilla/firefox/ is a file that saves all your preferences. It sounds like the permissions on that file is not set properly, so it cannot be saved. Unfortunately, I don't happen to know what file it is.

It's prefs.js.

---

### Post by barraclou on 2009-05-15
It might sound too obvious, but have you click OK after changing your homepage address?

---

### Post by dragos240 on 2009-05-16
I fixed it guys! I just reinstalled firefox and deleted .mozilla and it works now.

---

