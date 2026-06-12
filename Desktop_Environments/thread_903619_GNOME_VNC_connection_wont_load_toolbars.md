---
title: "GNOME VNC connection wont load toolbars"
date: 2008-08-28
forum: Desktop Environments
---

### Post by Malefic on 2008-08-28
With VNC being wonky I only have SSH access to this computer, so I can't verify if this is happening for remote users only.

When I connect I get the normal debian login screen, and all is well. It logs me in fine, and then I just get my wallpaper displayed. I can interact with the background via right clicks, and create folders etc, but my toolbars are not loading. 

Any help?

---

### Post by Malefic on 2008-08-28
bump* 

I've fiddled with xinetd a little to troubleshoot, can't make any headway.

Anyone have ideas?

---

### Post by MyR on 2008-08-29
Greetings!

Try restarting gnome-panel. I think it respawns if you just kill it.
Also, is compiz enabled? there were some issues with panels not being displayed although I haven't had any trouble with that in a while.

peace

---

### Post by Malefic on 2008-08-29
Solved, it was an issue with gnome-panels. Reinstalled it, fired it up and now all is working peachy.

Thank you.

---

