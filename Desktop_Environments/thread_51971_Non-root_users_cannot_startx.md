---
title: "Non-root users cannot startx"
date: 2005-07-25
forum: Desktop Environments
---

### Post by alagenchev on 2005-07-25
Hi, I don't know what  kind of ubuntu I have, warthy dog or whatever. I have 5.04. I try to start gnome under regular user, but it does not start, then I run failsafe and delete the file that is /tmp/whatever and do a startx again, but it tells me that the user is not authorized to startx. I can login as root without a problem. I even gave 777 permissions to startx, but that doesn't seem to help. Does anyone have any suggestions?

---

### Post by heimo on 2005-07-26
While waiting the knowledgable people to find your question, I might answer as well. :) This may be wrong or unsecure or both.

Can you run */etc/init.d/gdm start *and then login using your normal user? Is that acceptable solution?

Check /etc/X11/ directory, there should be file with name something like Xwrapper.conf and a line with allowed_users or similar, is its value rootonly? Change it to console or anybody. Try startx as a user.

Check permissions on ... can't remember it... something like /etc/X11R6/bin/X (probably), does it have suid or guid bit set? little s letter, something like rwxrsxrwx (use ls -l [filename]), if not, try setting it using chmod g+s [filename]

This will cause X to run with root priviledges, even when user invokes it (startx). (EDIT: this the file should be wrapper for starting X, and owner group root for this to work)

Please, other people, correct if I'm making mistakes. You should have suid-bit set only for wrapper (as far as I understand this), and not for the X server itself. If you set any suid bits that are unneeded or don't seem to make difference, remove those - they're security risk.

Sorry if my English is hard to understand. Hopefully the message gets through.

---

