---
title: "Artifacts left on desktop after switching to awm then back to Gnome"
date: 2010-08-13
forum: Desktop Environments
---

### Post by tmac303 on 2010-08-13
I recently tried out the awm version of the desktop environment. When I switched back to the Gnome desktop, I found a couple of titlebar-like artifacts left on the desktop.

I did some experimenting, using System Monitor and the Kill xxxx command and managed to rid myself of one of the artifacts. The remaining artifact can be taken care of by using kill xxxx comand for the gtk-window-decorator but, this basically renders window buttons useless after the command is issued.

I think I had a couple applications running at startup in Gnome desktop before I switched to awm, and they didn't start at startup when I returned to Gnome desktop, but the titlebar-like artifacts did.

Is there a way to reset the state of the gtk-window-decorator in a manner that is less destructive, and which allows my desktop to be clear of this artifact?

Thanks for any advice you might be able to offer in advance,

Terry

---

### Post by tmac303 on 2010-08-14
Found the answer myself by using "man gtk-window-decorator". Used "metacity --replace" in terminal and after shutting it down then rebooting, the artifact was removed.

---

