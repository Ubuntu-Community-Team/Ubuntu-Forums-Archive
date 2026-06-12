---
title: "Compiz/X11 Fail? Ctrl-Alt-Backspace? Help."
date: 2009-03-26
forum: General Help
---

### Post by antipuls3 on 2009-03-26
Compiz/X11 Fail? Help me get my desktop effects back on!
Hey guys! New, enthusiastic Ubuntu 8.10 user here! I just jumped on this past Satuday, and it's been pretty fun getting everything working. But then this afternoon something happened. My compiz stuff is gone and I can't turn on any more effects (suddenly) than the basic of basic desktop effects.

I hit Ctrl-Alt-Backspace because I wanted to know what it did. That shuts down X11, right? What do I do to turn it back on?

In the console, I try to start "compiz"

and get:

Checking for Xgl: not present.
Detected PCI ID for VGA:
Checking for texture_from_pixmap: not present.
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present.
aborting and using fallback: /usr/bin/metacity

{edit}Back from a fresh reboot. After running "compiz" above, my minimize, expand, and exit buttons on the upper right of all my windows disappeared, and I had to reboot. What the heck... I really with I hadn't hit Ctrl-Alt-Backspace. Haha..

Fail.

What am I doing wrong/what can I do to get on the right track? Thanks to all who can help me!

---

### Post by Xiong Chiamiov on 2009-03-27
Did you update the kernel recently?  What does /var/log/Xorg.log say?

---

