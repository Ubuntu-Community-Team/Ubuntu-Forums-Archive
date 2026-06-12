---
title: "Brief keyboard input hanging on every write to home directory"
date: 2009-04-29
forum: Desktop Environments
---

### Post by freakinhippie on 2009-04-29
I've been dealing with an issue for a few weeks now. Whenever I write any data into my home directory, it causes my system monitor applet to reset, and during the reset, the system stops responding to keyboard input. It seems to queue the input, but it just stops responding for about 2 seconds each time. This issue is 100% reproducible for me. I'm going to list some of my findings:

[LIST=1]
[*]Any data writes including creating or updating a directory or file, removing a directory or file trigger the behaviour. This is true, not just within my immediate home directory, but within any **unhidden** directory below it. Interestingly enough, it doesn't happen whenever data is written within a hidden (aka "dot") directory.

[*]The problem doesn't occur when logged into a fail-safe X session. (Which leads me to believe that it is a component of X.org/Gnome/Metacity/etc causing it).

[*]The problem doesn't exist for another (newly created, for testing) user of the system. However, when logged into the new user account, the problem *can* be triggered for the new user by becoming root, or my user and writing/removing data from my home directory.

[*]The problem does not seem to be a hardware problem, as I've copied all the data within my home directory to a new home directory, renamed my original home, then renamed the new home to the original name and the the problem persists when logged in using the newly created directory (which has identical content to the original home directory).

[*]I've not found a way to reproduce it anywhere outside of my home directory. For instance, writing to /home/ itself does not cause any problems. The same is true for /tmp/, /var/, and so on.

[*]Disabling Nautilus' draw the desktop feature does not seem to have any effect on this problem.

[*]Disabling all of the functionality within the Tracker Daemon (which is what I thought was the cause) does not have any effect on this problem. In fact, killing the daemon entirely doesn't help.

[*]The problem has persisted through various kernel updates.
[/LIST]

I would appreciate it if someone has some ideas on what could be causing this, or what I might do to remedy the situation. If I haven't provided any necessary information, please let me know.

Additional information:

[LIST]
[*]System is running Ubuntu 8.10 (upgraded from an original installation of 8.04).

[*]Kernel: 2.6.27-11-generic #1 SMP Wed Apr 1 20:57:48 UTC 2009 i686 GNU/Linux

[*]Desktop Effects are disabled.
[/LIST]

Thank you all!

---

