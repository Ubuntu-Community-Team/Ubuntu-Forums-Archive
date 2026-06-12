---
title: "What file(s) are changed when you select a different background?"
date: 2009-09-21
forum: Desktop Environments
---

### Post by protargol on 2009-09-21
When you change your background, I'm assuming you changed a file that directs to the background.  I am wondering where that file is and how can I figure out what background I had.

I got frustrated with my partitions and just reinstalled everything (I did a backup of the files first).  I had a cool background but don't know what it was called and couldn't find it in the folder I thought it was in.  I'm hoping I can find some file that points to it.  Thank you!

---

### Post by protargol on 2009-09-21
Ok, so I think I figured out my own question:

Here's what I referenced:
[http://ubuntuforums.org/showthread.php?t=844125](http://ubuntuforums.org/showthread.php?t=844125) (less helpful but got me on the right track)
[http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) (what solved my problem)

so gconftool and gconf-editor will help you find your current settings, but the go to files found in /etc/gconf and ~/.gconf.  Some digging in ~/.gconf and ~/.gconf/desktop/gnome/background is what I was looking for.  Hope this can help someone else

---

