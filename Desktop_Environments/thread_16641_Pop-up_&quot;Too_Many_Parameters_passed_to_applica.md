---
title: "Pop-up &quot;Too Many Parameters passed to application&quot;"
date: 2005-02-22
forum: Desktop Environments
---

### Post by reedlaw on 2005-02-22
Every time I start gnome I get an unidentified pop-up that says simply "Too Many Parameters passed to application".  There is no mention of which application.  I've looked at dmesg and still can't find out what it is.  Is there any way I can figure out what's causing this and then fix it?

**Edit:**  I have discovered it was Gaim, set to auto-login to MSN.  I disabled auto-login and now I don't get the popup anymore.  Now how to find out why it was there in the first place so I can re-enable auto-login...

---

### Post by Wim Sturkenboom on 2005-02-23
What does the line look like that starts gaim? Check against *man gaim*.

---

