---
title: "&quot;Samba guest account&quot; instead of MY account on login screen"
date: 2013-05-13
forum: Desktop Environments
---

### Post by dargaud on 2013-05-13
Hello all,
I upgraded a system to the latest kubuntu yesterday without a hitch.

Then today I did the do-release-upgrade to my main work PC... and things got weird after reboot. On the login screen I only get two login possibilities: "Samba guest account" (which doesn't work) and "Guest" (which works and I'm using right now to post this cry for help), a [KDE Plasma Workspace] button which does nothing but alternate between bold typeface and not, and 3 Sleep/Restart/Shutdown buttons which don't work.

I can't enter my username in order to login !!!
I can login in a konsole (Ctrl-Alt-F2, or ssh from a graphic console) so my account is not nuked.

What happened ?!? And how do I fix it ?
Thanks.

---

### Post by dargaud on 2013-05-13
OK, I managed to ssh into my account from guest, launch systemsettings as root and set the greeting manager to 'classic'.

---

