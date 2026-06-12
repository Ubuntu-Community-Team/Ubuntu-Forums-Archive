---
title: "Xorg high CPU usage -- vino-server"
date: 2011-05-02
forum: Desktop Environments
---

### Post by joosteto on 2011-05-02
Dear forum,

For I think more than a year now I'v experienced high Xorg CPU usage (around 15--25%, constantly, even without anything enabled,
even when viewing 'top' from a virtual console).
After upgrading to Natty Narwhal (and the problem persisted) I decided to kill processes until CPU usage would drop. Turns out that just doing

killall vino-server

makes Xorg go out of my 'top' list altogether (from a VC, or to 0.5--2.0% when viewed from a gnome-terminal).

Killing vino-server works again even after a reboot, with all other usual processes running.

So, somehow vino-server (from the vino package) makes my Xorg eat  CPU. I've filed a bug-buddy report too, but thought reporting it here might help other people searching for the same problem.

---

