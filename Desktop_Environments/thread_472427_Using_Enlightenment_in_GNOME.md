---
title: "Using Enlightenment in GNOME"
date: 2007-06-13
forum: Desktop Environments
---

### Post by Sweet Mercury on 2007-06-13
(Forgive the lack of detail, I had typed up a long, detailed post explaining my situation, but either an admin deleted it or the forum ate it.)

I would like to experiment with replacing Metacity with Enlightenment (or Xfwm4, or maybe something else), in GNOME. I installed the Enlightenment package through Synaptic. It created a few new sessions, and Enlightenment session and an E-GNOME session (gnome with enlightenment).

The Enlightenment only session is completely bare-bones, and only half functional.

The E-GNOME session is, unfortunately, identical to the regular GNOME session--according to the system monitor, Metacity, not E, was running.

So, how do I switch the Window-manager (or panel-manager, or any other aspect) within a session? I had assumed it would happen automatically on install.

---

### Post by trippinnik on 2007-06-13
try entering gnome-session-remove metacity in the terminal then enter enlightenment, this should replace the window manager.  i've done it before by following this thread: [http://ubuntuforums.org/showthread.php?t=54476&highlight=howto+enlightenment+replace+metacity](http://ubuntuforums.org/showthread.php?t=54476&highlight=howto+enlightenment+replace+metacity) and this one for xfwm4.  You might also want to check out E17, the development version of Enlightenment it's actually really good, but sometimes a little unstable and rapidly changing otherwise it's a valid replacement for GNOME or KDE but is lightweight and has great appearance.

---

### Post by Sweet Mercury on 2007-06-13
Thanks. I'll give that a try. Can I do that with other aspects of the DE as well?

---

### Post by Sweet Mercury on 2007-06-14
Here's another related question.

With this mixing and matching I'm trying (haven't succeeded yet but I'll get there), I'd like to create my own custom sessions while leaving the original GNOME session intact for safety.

Is there a simple (or complex, I'm willing to learn some) way to do this? As of now, all my sessions were created automatically.

Also, how can I change my "Xclient Script" Session to point back to GNOME. Enlightenment pointed it to my "Enlightnment (only)" session?

(Or should this all be a new thread, not sure how the mods prefer it ere...)

---

