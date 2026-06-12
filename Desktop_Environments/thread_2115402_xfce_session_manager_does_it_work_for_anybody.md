---
title: "xfce session manager: does it work for anybody?"
date: 2013-02-12
forum: Desktop Environments
---

### Post by r.stiltskin on 2013-02-12
The xfce4-session-manager in 12.04 (64 bit) seems very broken.  In Settings Manager/Session and Startup the logout settings "Automatically save session on logout" and "Prompt on logout" have no effect: whether they are checked or unchecked it *never* saves automatically and it *always* prompts "are you sure ..." on logout.

I can manually save the current session by going to the Session tab and clicking "save session", but on login it disregards the Workspace location of running applications and opens everything in Workspace 1.

And it doesn't shut down applications nicely -- basically just kills them.  If Firefox is open when I logout (and if it is part of a manually saved session or set to autostart), when it reopens it has to recover all previously-open tabs.

---

### Post by r.stiltskin on 2013-02-13
So, partially answering my own question, it turns out that after adding an Action Button (logout) to the main panel, if I log out from Workspace 1 the session is saved (even without checking "automatically save session" in the settings manager) and programs are restarted in the correct workspaces upon login.

But they are still not shut down properly on logout, just killed.

---

### Post by r.stiltskin on 2013-02-13
This was originally installed as Kubuntu but then I uninstalled kubuntu-desktop and it's dependencies and installed xubuntu-desktop, so apparently something got messed up in that changeover.  After trying for a while to straighten it out I ended up breaking the xfce4 panel and desktop even worse.

Got tired of wasting time & did a clean install of Xubuntu 12.10 and everything seems to be working & playing together nicely now -- including the KDE apps that I "must have" (Kile, Kate, Konsole and Dolphin).  So I would call it more or less "solved".  Probably a clean install of Xubuntu 12.04 would have worked too, but I didn't try that so can't say for sure.

Except the Firefox messy-shutdown issue, but that seems to be a Firefox problem, not an XFCE error.  Chrome, and every other program I've tried, seem to have no difficulty when shut down just by logging out.

---

