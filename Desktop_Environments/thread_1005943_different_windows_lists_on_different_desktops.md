---
title: "different windows lists on different desktops?"
date: 2008-12-08
forum: Desktop Environments
---

### Post by davbren on 2008-12-08
Is there a way of giving an external monitor a separate window list that only looks at the apps that are present on that desktop? rather than all the apps that are currently open?

---

### Post by Ng Oon-Ee on 2008-12-09
It depends. Not if you're using Twinview or Xinerama (or their ATI equivalents), since your whole desktop is a single desktop to the POV of many apps.

If you're using separate x-screens (like I am) then it happens by default. But then you can't drag from monitor to monitor and URLs in one monitor won't open in Firefox on another.

Trade-offs, all round.

---

### Post by davbren on 2008-12-09
Well, on windows theres a program that allows this to happen? I think its really useful, even on twinview. I have no idea how to go about it, but it must be possible...

---

### Post by Ng Oon-Ee on 2008-12-09
Yes, on Windows. A whole-ly separate OS. Linux OS-es are based on X11 for graphical output, and X11 is inherently multi-terminal, which is to say, it was designed for running multiple x-screens. Which means that all apps are tied to their screen, because its not just about the appearance, things like IDs and stuff are tied there as well. This initially made sense so that you could have X-sessions from different computers and stuff. However, with dual and up monitors, this behaviour wasn't very useful for most normal users, so Xinerama and Twinview were developed by NVidia. Basically, both of these emulate a single x-screen, but divide its output to appear on 2 or more monitors. However, barring major changes to X11, this x-screen appears to be a SINGLE one to apps.

The correct forum to ask about 'moving apps between x-screens' would actually be the one for X11. Its more likely an IRC chat or mailing list though. I haven't really asked.

About Twinview, I really doubt it would be possible without your own custom coding. Perhaps you could do it in Compiz, by checking bounds on the window, but I have no idea how.

---

