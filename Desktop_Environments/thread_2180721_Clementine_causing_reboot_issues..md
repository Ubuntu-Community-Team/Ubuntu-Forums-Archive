---
title: "Clementine causing reboot issues."
date: 2013-10-14
forum: Desktop Environments
---

### Post by lastlion on 2013-10-14
I have been using 12.04 for a while, just did a few new installs.  On my main box I decided to try Clementine and I love it except for the fact it causes issues when I shutdown/reboot.

When I "restart" for example Clementine will disappear but all other apps will stay open.  If I click "restart" again it'll reboot just fine, but it takes two restarts when Clementine is open.

Also, Ubuntu is clearly in an odd state after the first restart attempt doesn't work.  Tried launching some apps and stuff and the UI slowly starts losing functionality.

---

### Post by lastlion on 2013-10-14
So I just removed and then re-installed Clementine and issue is resolved.  Computer restarts/shuts down when Clementine is playing.  I delayed this action because I didn't want to recustomize Clementine but all my settings were there after reinstall.

I removed via the UBuntu Software Centre and installed from CLI, not sure if that makes any difference.

---

### Post by lastlion on 2013-10-14
Well, spoke too soon.  That worked for a reboot or two now it's back to hanging on restart/shutdown.  The restart/shutdown does not hang indefinitely.  Ubuntu will sit there for a while (long enough to trick you into thinking it isn't shuttin down) and eventually it'll reboot.  Why does it hang? I've narrowed it down to Clementine...

---

### Post by lastlion on 2013-10-14
When I issue the shutdown command from terminal there is no issue.  The problem is when shutting down of app from menu.

---

