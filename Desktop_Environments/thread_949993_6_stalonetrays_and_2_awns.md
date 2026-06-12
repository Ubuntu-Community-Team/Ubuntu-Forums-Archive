---
title: "6 stalonetrays and 2 awns?"
date: 2008-10-16
forum: Desktop Environments
---

### Post by Sam Lars on 2008-10-16
Whenever I log into XFCE, it starts 6 stalone trays (they all show up in the compiz scale plugin), and I can see at least two avant window navigators rolling in.  I have to do a killall and then start 1 of each.
I can't find anything simple like Gnome's session manager that's starting these... what do I need to do to stop these things from starting so many times?

---

### Post by denham2010 on 2008-10-16
Sounds like you have had the "Save sesion" option active at one stage.

To fix the issue:

Firstly, open the "Sessions and Startup" module in the XFCE Settings Manager.

Ensure the "Automatically save session on logout" option is ticked.

Now open the "Autostarted apps" module and make sure every item you have added in there (not the default items) is unticked.

Next, close all running applications, including stalonetray and awn (you should have not tasks showing on the task bar or in your tray).

Re-start the computer.

Reopen the "Sessions and Startup" module and untick "Automatically save session on logout" and restart the computer again.

Now, open the "Autostarted apps" module and tick all the items you added in there. Add an autostart item for awn and stalonetray if not already there.

Restart once again and it should all be fine.


I know this is a long-winded process, but the save session option combined with applications "auto startup" options and the "Autostarted apps" module causes nothing but trouble as it remembers everything you had running at shutdown, and then will restart all those items along with everything you have set to autostart.

I simply do not use the save session option at all, as it generally causes nothing but frustration.

Cheers.

---

### Post by Sam Lars on 2008-10-17
Thanks for the help.
I may find it if I look, but where is the Autostarted Apps module located?

---

