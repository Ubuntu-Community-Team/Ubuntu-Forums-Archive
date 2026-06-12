---
title: "No auto-launch for one specific app"
date: 2010-02-02
forum: Desktop Environments
---

### Post by dargaud on 2010-02-02
Hello all,
I do not want Amarok to launch when my session start. The reason is that the disk with the music on is not mounted at this stage and Amarok loses the whole library if it doesn't see the disk and I have to rescan the whole thing.

I remember reading that there's a way to take actions on KDE login/logout, but I can't find the info right now. I should just place a 'Killall Amarok' in the logout script, right ?

Any suggestion appreciated (maybe there's a way to get Amarok to ignore unmounted disks, or a list of no-run apps for the autolaunch).

---

### Post by Zorael on 2010-02-02
I always start with an empty session myself, so can't confirm that it works, but try entering **amarok** into the input field at System Settings -> Advanced tab -> Session Manager -> Applications to be excluded from sessions.

---

### Post by dargaud on 2010-02-02
Thank you, I'll give it a shot on next reboot although the syntax is not explicited if you want to exclude more than one app.

---

### Post by Zorael on 2010-02-02
From #kde@irc.freenode.net;
```
[15:24] <Zorael> How do you separate several apps from being exempted from session restore? (System Settings -> Advanced tab -> Session Manager -> Applications to be excluded from sessions.)
[15:24] <Zorael> Comma? Space?
[15:25] <pinotree> see the "what's this" in the lineedit
[15:25] <pinotree> (comma should be)
[15:25] <Jucato> or colon (it says) but I think comma (without space in between) is the one that works
```

---

