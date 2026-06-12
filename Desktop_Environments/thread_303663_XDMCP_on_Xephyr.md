---
title: "XDMCP on Xephyr?"
date: 2006-11-20
forum: Desktop Environments
---

### Post by dreweinhorn on 2006-11-20
The ubuntu-users list seems to have decided my gmail account belongs to
a spammer, and seems to be silently dropping posts from it.  Or maybe it
more complicated than that.  Anyway I'm running away from that problem.

When I wrote the following I was on Dapper, upgraded to Edgy, going
back to Dapper.  Edgy crashes and freezes way too often.

----------------------------------

Running Dual Head with 1440x900 lcd and a big old Dell Trinitron crt
at 1600x1200.

I've got about a half dozen boxes, and I run:

   gdmflexiserver -n -l

to bring up an Xnest window containing a gdm login for the local box.

Would rather it took me straight to the "Remote Login via XDMCP".

What I really want it to do is put the gdm login in an Xephyr window
instead of an Xnest window.  Then randr will work and I can use the
Screen Resolution gui to tweak my real estate.

Would like be able to drag windows from screen to screen, but when I try
turning Xinerama on the screen resolution/refresh gets whacked out and
I can't see what I'm doing, and randr doesn't work, and I've got plenty
of other stuff to do.

Also I'd like the TitleBar on the window to say Xnest@host instead of
just Xnest, but I'm trying to switch from Xnest to Xephyr anyway so
maybe that will come out in the wash.

Drew

---

### Post by demonbane on 2007-03-10
Wow Drew, you seem to be really unpopular... :) I was actually just trying to do this very thing and I kept coming across your posts on Google and it seems no one ever responded. So for the benefit of future Googler's, here's what I finally managed to figure out. :)

To use Xephyr to connect to a remote machine via XDMCP directly do:

Xephyr -query servername :1

(You may need to change :1 to a different available display)

To use Xephyr to run a local gdmchooser instance do:

Xephyr :1 &
/usr/lib/gdm/gdmchooser

One problem with this approach is that the gdmchooser appears to be braindead. It'll run, and let you select a server, but then it doesn't actually connect you to the appropriate server. I'm still working on that bit. But for the time being I can at least connect to a running version of GDM on another machine so I'm happy.

---

