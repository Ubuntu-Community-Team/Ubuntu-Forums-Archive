---
title: "Something has gone horribly wrong with the window manager (Xubuntu 8.10 AMD64)"
date: 2009-04-11
forum: Desktop Environments
---

### Post by ringokamens on 2009-04-11
Hey Folks,

I'm running on the most recent Xubuntu version and something weird happened last night. Had a few programs open (I believe Miro, Firefox, and Thunderbird) and all of the sudden they all ceased to have title bars. What's more, I can't switch between them even using Alt+Tab. The top window just stays on top. There's also no application menu at the top unless there are no windows.

I tried logging out as well as restarting, none of which fixed the problem. I tried doing a ctrl+alt+backspace to restart x but I still got the same problems.

This has pretty much made my machine worthless. Any ideas? Is there a cache/settings area I can clear or something?

Thanks for any help you can offer,

Ringo

---

### Post by morgengenuss on 2009-04-11
sounds like xfwm4 (xfce's window manager) crashed.
you should be able to restore it by opening a terminal (or even better pressing alt+f2) and executing "xfwm4".

save your session on logout just in case xfwm4 is not there when you logout and login back again.

---

