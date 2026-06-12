---
title: "Hyperlinks not working with FF1.5"
date: 2006-02-07
forum: Desktop Environments
---

### Post by 8bit on 2006-02-07
I installed FF1.5 since my older version kept closing out on me from time to time. The problem I have now is that if I click a link say in an email from someone, it opens FireFox and my startup page (google). It doesn't load the link or webpage that the link is pointing to.

I had this problem before but can't remember what I did to fix it.

Can anyone help?

---

### Post by juancnuno on 2006-02-07
System - Preferences - Preferred Applications

In the custom command field, make sure there's a %s after the firefox command.  That %s passes the URL to the firefox executable, which it then opens.

---

### Post by PapaWiskas on 2006-02-07
[http://ubuntuforums.org/showthread.php?t=126544](http://ubuntuforums.org/showthread.php?t=126544)

This is what I did...

---

### Post by 8bit on 2006-02-07
That did it. Thanks a million!

---

