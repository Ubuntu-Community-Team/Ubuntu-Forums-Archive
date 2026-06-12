---
title: "VNC &quot;unique&quot; gnome sessions"
date: 2009-12-28
forum: Desktop Environments
---

### Post by thanatoast on 2009-12-28
Hello,
  Is it possible to use vnc (specifically tightvncserver) to create a unique gnome session? What I mean is, I am already logged in to gnome as a specific user (and therefore using ~/.gnome2/* files and ~/.gconf/*, and whatever other files). If I run tightvncserver it creates a new session but, that session is using those same files. Can I tell tightvncserver to use some other directory (like ~/vncstuff/.gnome2, etc) so that changes that are made in one session don't mess up the other?

(I ran tightvncserver and it looked great on the remote machine but, apparently, it messed up my gnome panel: ended up with multiple copies of the panel, none of which could be deleted...It's fixed, now.)

The reason for wanting to do this is that I want to control a music player in gnome remotely (I didn't find a web plugin I liked for any of them).  I already tried this using a different user but, the sound would not work in both sessions.  Sounds seem to work fine in both sessions when I use the same user.  I will be accessing the vnc server using a pocket pc over wireless, so I would like the vnc session to be quite a bit different.

If this is possible, would someone tell me how, or where to find information about this?

Thanks in advance.
Russ.

Oh, this is on Jaunty.

---

