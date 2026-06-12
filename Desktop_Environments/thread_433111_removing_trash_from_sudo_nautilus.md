---
title: "removing trash from sudo nautilus"
date: 2007-05-04
forum: Desktop Environments
---

### Post by goneskiing on 2007-05-04
when I'm using sudo nautilus and move files to trash, where do they go ?  They do not seem to go into the current user's trash bin.  If they go into root's trash bin, how do I empty it ?  or even delete the file ?

---

### Post by floke on 2007-05-04
They go to root trash - so navigate to the root desktop etc. and you'll find it around there.

---

### Post by aysiu on 2007-05-04
They go to /root/.Trash

By the way, use ```
gksudo nautilus
``` instead of ```
sudo nautilus
``` More info here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by goneskiing on 2007-05-04
Ahhh, thks so much guys.  I had a 22 gb log file trapped in there and it was killing my logins.   The log file was a Cups log file (don't ask me how it got created - maybe when I had to restart a print job - or just Friday gremlins).   Anyway I really, really appreciate your fast responses.  Ubuntu forum members are great.

ps: and thks for the link on gksudo - now I understand the difference.

---

