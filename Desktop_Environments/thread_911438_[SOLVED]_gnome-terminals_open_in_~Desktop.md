---
title: "[SOLVED] gnome-terminals open in ~/Desktop ???"
date: 2008-09-05
forum: Desktop Environments
---

### Post by renauldo on 2008-09-05
After upgrading to hardy, all my gnome-terminals default to being in ~/Desktop instead of $HOME.  WTF?

How do I make the pain go away?  This ~/Desktop insanity hurts me bad.  I am bleeding inside.  In my spleen.  Also, in the kidneys.

Note that launching an xterm /doesn't/ end up in ~/Desktop, but rather, in $HOME proper.  As it should.

---

### Post by yjwong on 2008-09-05
I'm not too sure about this; but by any chance, do you have a custom command set for your Terminal profile? You can check this by going to Edit -> Current Profile... in GNOME Terminal. It is under the "Titles and Command" tab.

---

### Post by renauldo on 2008-09-05
> **yjwong said:**
> I'm not too sure about this; but by any chance, do you have a custom command set for your Terminal profile? You can check this by going to Edit -> Current Profile... in GNOME Terminal. It is under the "Titles and Command" tab.

thanks for the idea, but alas, the only thing checked is "Update login records when command is launched," and unchecking that doesn't seem to help.

I've been grepping through dot files and clicking through gconf to see where this could be getting set, but find nothing...

---

### Post by renauldo on 2008-09-05
holy crap, this was an intentional upstream change!?  WHAT WERE THEY THINKING?

[http://lists4.opensuse.org/opensuse-bugs/2008-04/msg04502.html](http://lists4.opensuse.org/opensuse-bugs/2008-04/msg04502.html)

At least I know who to send the spleen-repair bill to now.

---

