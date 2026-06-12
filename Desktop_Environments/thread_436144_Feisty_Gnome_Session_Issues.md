---
title: "Feisty Gnome Session Issues"
date: 2007-05-07
forum: Desktop Environments
---

### Post by cdrom600 on 2007-05-07
I have a somewhat complicated issue.  I've been researching and learning for hours and hours now, and I hope I've gathered enough information for someone to help me out.

I recently upgraded (through the Update Manager) to Ubuntu Feisty (7.04).  I now have a problem.  When I log in to the default "Run Xclient" session or the "Gnome" session, my desktop loads, but the loading dialog (with icons for Metacity, Nautilus, etc.) stays on the screen.  Metacity does not load, so any windows I have do not have borders or title bars.  (Running "metacity --replace" in a terminal launches Metacity, though.)
My session's startup programs don't load either (Network Manager, Bluetooth Configuration, etc...).  However, if I wait about 70 seconds, my session continues to load normally, with the Network Manager, etc. starting.  I have the Beryl Manager set to load with my session, and it also starts after 70 seconds.  It loads metacity (I have it set to load metacity if it detects that there is no window manager running).

I will attempt to give you everything I know about this problem.
- I am not running Beryl by default, although I keep the Beryl Manager running in the system tray so that I can easily start Beryl if I want.
- I've seen suggestions of removing the ~/.gnome2/session file, as well as removing the ~/.gnome2_private folder.  Neither of these work.
- I do not have the "Automatically save changes to session" box checked in the Sessions preferences dialog.
- If I create a new user and log into his account, the session loads normally, so this problem only affects my account; it is not a system-wide issue.
- If I log into the Failsafe GNOME session, the problem does not occur.  It occurs when logging into the "Run Xclient" or "GNOME" sessions.

I suspect that there is a user session configuration file which is corrupt or otherwise invalid, or that there is a problem with a session or logon script somewhere.  Unfortunately, I don't know enough about Gnome to even know where to look to begin further debugging.

Any help is appreciated.

*(I've attached a bootchart log; I don't know if it'll be useful, but I don't know.)*

---

### Post by cdrom600 on 2007-05-07
Checking the "Automatically save changes to current session" box does not fix the problem; instead, I get the problem which users have described which requires that I delete the ~/.gnome2/session file.

---

### Post by Turin Turambar on 2007-05-08
I have the very same issue. I deleted the session file and will now restart and see if it's any better.

---

### Post by ezuli on 2007-05-08
I have same problem. I tried everything logical; reinstalling some gnome-stuff, deleting gnome-files from homedir, reconfiguring everything with dpkg-reconfigure. Then I got tired with mess and installed Kubuntu and remove Ubuntu (via apt-get.) Then I installed Abiword again (as simple and usefull gnome app), but it was still unuseable. It worked, but were terrible slow. (Writing less than 1char per sec)

---

### Post by klato on 2007-05-08
I've got this exact same issue...metacity and network manager don't come up unless I turn metacity on from beryl-manager!  All other users seem to be ok.

---

### Post by cdrom600 on 2007-05-08
Possible solution: see this message: [http://ubuntuforums.org/showthread.php?p=2614868#post2614868]("http://ubuntuforums.org/showthread.php?p=2614868#post2614868").  This fixed the problem for me; YMMV.

---

### Post by Omegatron on 2007-05-15
I have the same problem.

---

