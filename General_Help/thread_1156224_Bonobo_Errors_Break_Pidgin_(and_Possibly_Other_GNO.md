---
title: "Bonobo Errors Break Pidgin (and Possibly Other GNOME Programs)"
date: 2009-05-11
forum: General Help
---

### Post by GenuineXP on 2009-05-11
I'm using Ubuntu 9.04 (Jaunty) AMD64.

For some reason, Pidgin decides to freeze up almost instantly at random times. It seems to happen during long sessions (e.g., if the computer is left running overnight), but I can't be sure just yet. Pidgin will stop responding and I need to send a terminate signal. After that, it can't be started again; the tray shows two blank slots (but no icon) and it refuses to start.

When launched from a terminal after this occurs, I get an error message concerning Bonobo. I don't have the error message now since I've already made it a habit of logging out and back in to fix the issue. The next time it happens, I'll post it.

Has anyone else experienced this? Any ideas how to solve it? I'm not sure if this is related, but GNOME Do also seems to randomly crash out of existence after longer sessions. I may start a separate thread about that. On one occasion, just about everything stopped responding, including the GNOME Panel. I never experienced anything like this in previous releases.

Thanks.

---

### Post by GenuineXP on 2009-05-11
Bump. :)

---

### Post by GenuineXP on 2009-05-11
Something is killing GNOME Panel entirely and I think it may be related. Does anyone know about any Bonobo related bugs floating around Jaunty? At this very moment, my entire panel is unresponsive and it keeps happening.

Any help is appreciated. Thanks again.

**EDIT**: Alright, so the panel crashes whenever I actually click on the Clock applet. I restarted it and everything seemed okay, but once I click on that applet to view my calendar it stops the whole panel in its tracks. Strange.

---

### Post by GenuineXP on 2009-05-12
Wow, this is getting frustrating. Any programs linked to the panel are breaking. I was just in the middle of a conversation when Pidgin locked up. The panel froze, including the Clock applet along with Evolution!

Here's what Pidgin gave me from a terminal (finally saved it):

```
sean@fafnir:~$ killall -9 pidgin
sean@fafnir:~$ pidgin 
^C
(pidgin:9505): Bonobo-WARNING **: Leaked a total of 1 refs to 1 bonobo object(s)

```

Any ideas? I'm getting desperate. I have to keep logging out and back in.

---

### Post by spinstartshere on 2009-07-20
I just experienced this problem and it went when I restarted my computer.

---

### Post by GenuineXP on 2009-10-16
This still occasionally occurs for me. :-( Karmic is coming soon, and I'm hoping that the updates to GNOME somehow fix this problem. Has anyone else experienced this (or something similar)? It can be very irritating, especially since the entire panel and Evolution all break.

Is Bonobo likely the problem? It looks like the GNOME dev team is pushing to deprecate and replace Bonobo as quickly as possible.

---

