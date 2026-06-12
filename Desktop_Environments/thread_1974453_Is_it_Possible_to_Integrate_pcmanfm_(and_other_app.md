---
title: "Is it Possible to Integrate pcmanfm (and other apps) into Xfce Session?"
date: 2012-05-06
forum: Desktop Environments
---

### Post by ohnonot on 2012-05-06
meaning:

in settings manager -> session and startup -> session

i find a list of applications and what to do when they accidentally terminate or crash (restart style).
with thunar it had the effect that if thunar crashes, it gets restarted immediately.
i want this behavior for pcmanfm, but there's no way of manually adding it to that list.
if i save the session and restart it still doesn't show up on the list.

so the question is:

how can i add applications to this list? i can remove them by pressing first quit and then save session.
i can add those native to xfce4, but how about others?

[IMG]http://i.imgur.com/Q659a.png[/IMG]

---

### Post by brainwash on 2012-05-06
PCManFM won't show up on the session list, because it does not implement the session protocol. Here is the "official" thread:

[http://forum.xfce.org/viewtopic.php?id=7011](http://forum.xfce.org/viewtopic.php?id=7011)

I replaced Thunar with PCManFM long time ago. It does not crash on my system (like never), so there was no need for me to try integrating it into the XFCE session or to write a separate background script which handles the restart behavior.

---

### Post by mips on 2012-05-06
> **brainwash said:**
> 
I replaced Thunar with PCManFM long time ago. It does not crash on my system (like never), so there was no need for me to try integrating it into the XFCE session or to write a separate background script which handles the restart behavior.

You should give SpaceFM a spin, really cool!
[http://ubuntuforums.org/showpost.php?p=11908624&postcount=25](http://ubuntuforums.org/showpost.php?p=11908624&postcount=25)

---

### Post by brainwash on 2012-05-06
Yeah, SpaceFM is a great file manager, but switching to it won't solve the actual problem (session integration).

---

### Post by mips on 2012-05-06
> **brainwash said:**
> Yeah, SpaceFM is a great file manager, **but switching to it won't solve the actual problem (session integration).**

Not what I was implying if it sounded that way, just mentioning spacefm ;)

---

### Post by ohnonot on 2012-05-07
> **brainwash said:**
> PCManFM won't show up on the session list, because it does not implement the session protocol. Here is the "official" thread:

[http://forum.xfce.org/viewtopic.php?id=7011](http://forum.xfce.org/viewtopic.php?id=7011)

I replaced Thunar with PCManFM long time ago. It does not crash on my system (like never), so there was no need for me to try integrating it into the XFCE session or to write a separate background script which handles the restart behavior.

yeah i've seen that thread and was wondering about session management - probably i'm not going to start rewriting pcmanfm.
;-)
...maybe i'll give that script a try, you have any idea how i would start writing that?
and thanks.

edit: forgot to mention that pcmanfm is also managing the desktop on my machine.

---

### Post by brainwash on 2012-05-07
Not sure yet, how to implement such a restart managment for both desktop and normal window instance.

Restarting the desktop shouldn't be a problem. Something like this could do the job:
```
#!/bin/bash

while true; do
  pidof pcmanfm && sleep 5 || pcmanfm --desktop
done
```

Run this script on startup (autostart or xinitrc) to spawn a persistent pcmanfm process. The infinite loop will restore the desktop, if it somehow dies.

---

### Post by ohnonot on 2012-05-11
> **brainwash said:**
> Restarting the desktop shouldn't be a problem. Something like this could do the job:
```
#!/bin/bash

while true; do
  pidof pcmanfm && sleep 5 || pcmanfm --desktop
done
```Run this script on startup (autostart or xinitrc) to spawn a persistent pcmanfm process. The infinite loop will restore the desktop, if it somehow dies.thanks.
that means it would get restarted every 5 secs if not running?

anyhow the problem is really rather with pcmanfm itself - it seems prone to crashing when used as file manager + desktop manager at the same time. the same with spacefm (which is a really great fm otherwise).
i was thinking of using pcmanfm for the desktop and spacefm as a file manager but clicking a folder on the desktop still opens pcmanfm even if i symlink it to spacefm.
(the same for xfdesktop - it always opens Thunar - is it possible to customize that?)

i searched session protocol, not much info on the xfce pages.
seems to have sth to do with entries in desktop files?!

---

### Post by brainwash on 2012-05-11
> **ohnonot said:**
> that means it would get restarted every 5 secs if not running

The command starts pcmanfm (desktop mode), if there is no pcmanfm process running. Otherwise it will query the process list every 5 seconds (loop) and restart pcmanfm only if needed.

By the way, are the crashes reproducible and did you try to debug them using GDB?

---

### Post by ohnonot on 2012-05-12
right now i'm back to thunar 
:cry:
and i've never used a debugger.

@mips: have you tried spacefm as desktop manager?

---

