---
title: "Firefox 4.0 Issue...has this happened before?"
date: 2011-05-23
forum: Desktop Environments
---

### Post by throese on 2011-05-23
Everything is explained in the attached image within this post.

---

### Post by lovinglinux on 2011-05-25
Try this:

[LIST]
[*]close Firefox
[*]open ~/.mozilla/firefox folder, which is hidden under your user home
[*]locate the default profile folder and open it
[*]locate the file *places.sqlite* and rename it to *places.sqlite.old*
[*]start Firefox
[/LIST]

At this point, everything should be fine, however you will have no bookmarks. to regain your bookmarks:

[LIST]
[*]open Firefox bookmark manager (CTRL+SHIFT+O) click "Import & Backup >> Restore" and select the latest backup in the list.
[/LIST]

---

### Post by throese on 2011-05-26
Well, I just did a regular restart of my computer because at the time I had to go to bed and it went back to normal the next day but thank you very much I'll keep your idea in mind in case it happens again. I always back up personal files and directories on an external drive and to back up programs I use Remastersys. =)

---

