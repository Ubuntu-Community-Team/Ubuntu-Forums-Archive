---
title: "KDE under LTSP, Ubuntu 12.10"
date: 2013-02-13
forum: Desktop Environments
---

### Post by asdf32 on 2013-02-13
I'm running Ubuntu 12.10 and trying to use remote X sessions with LTSP and KDE.  Unfortunately KDE is painfully slow.  Has anyone got remote X sessions for KDE working well?  I'm running over a gigabit network, so I would have expected a near-native experience.

By "painfully slow" I mean that switching between two overlapping windows can take 1-2 seconds.  Scrolling in Firefox appears not to be too bad (GTK app?), but scrolling in rekonq is very choppy.  Looking at "ifstat" on the server Firefox scrolling uses 400 KB/s, while rekonq uses about 10,000 KB/s.

I've tried a few things:
- turned off SSH tunnelling (LDM_DIRECTX=True) for LTSP
- switch QT into "native" mode (QT_GRAPHICSSYSTEM=native)
- installing OpenBox and logging in with a KDE/OpenBox session improves things considerably - I can switch windows at near-native speeds, but it still isn't great.

Running "ifstat" shows what seems to be a remarkably high amount of network traffic even with OpenBox as the window manager, and either way resizing windows is very slow.

Has anyone managed to get KDE working at a decent speed on a remote X session?

---

