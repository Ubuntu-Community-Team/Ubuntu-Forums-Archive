---
title: "Xubuntu 11.10 startup/shutdown issues"
date: 2011-11-08
forum: Desktop Environments
---

### Post by TrevP on 2011-11-08
I'm enjoying using Xubuntu 11.10 but there is a very annoying issue with startup and shutdown. When the computer is shut down, the computer often appears to "freeze" for about 30 seconds and then continues to shut down. On restarting the computer, the Xfce interface always starts without running xfwm4 (no title bars on windows and all windows in upper left corner of screen and immobile). I have to start it manually from a terminal. I have tried some of the suggested remedies (xfwm4 --replace and rm -r ~/.cache/sessions) but none of them fix the problem.

I can "work around" the bug by including xfwm4 in the startup programs but I would prefer a system that worked properly. I am currently investigating whether the issue is triggered by the monitor being blanked after 10 minutes idle (i.e. that the power manager is triggering the bug on my system). Meanwhile, if anyone else has had this issue and found a resolution for it, I would be grateful if you could enlighten me as to the cause.

---

### Post by TrevP on 2011-11-08
Just a quick update: I've checked the Xfce wiki and this issue is a known bug (it's a combination of Bug ID 7915 and 7687). The currently recommended work-around is to do what I have done and include xfwm4 in the list of programs launched at startup.

---

