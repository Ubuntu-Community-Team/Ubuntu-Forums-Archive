---
title: "Ubuntu 14.04 + Fluxbox inside GNOME?"
date: 2014-07-16
forum: Desktop Environments
---

### Post by stefan32 on 2014-07-16
Before I begin, I should explain what my final goal is.  I installed clusterssh for managing multiple servers with more efficiency.  I also have dsh installed.  The dsh install is great for batch processing, but clusterssh is sometimes needed for things that require interactive input (like changing a password with "passwd" on all servers at one time.)  My one problem with clusterssh is that it spawns every terminal as a new window.  It does nothing to shove the terminals into a tabbed window (like terminator, konsole, etc can handle.)  Getting clusterssh to use a different terminal is non-trivial as it expects the terminal to accept flags that xterm needs.

In researching this problem, I came across this post which explains how to use fluxbox to automatically group xterms into a tabbed window for you:
[http://www.edwiget.name/2011/11/administration-clusterssh/](http://www.edwiget.name/2011/11/administration-clusterssh/)

I prefer to keep GNOME running as a desktop manager.  I would like to be able to replace the window manager it uses (metacity, I believe) with fluxbox specifically so I can gain this functionality.  Every single tutorial I have found for doing this was for an older version of GNOME that required either copying a session file and making changes to it, or using gconf-editor to change the setting needed.  Unfortunately, that doesn't seem to work for the newer version of GNOME included with 14.04.  I see that gconf-editor is being phased out in favor of dconf-editor, but I can't find a document to describe how to change the window manager inside that.  I know I can log out and log back in to a fluxbox session, but I want to keep gnome... I just want to drop metacity.

I have read that openbox works nicely with gnome and is very similar to fluxbox, but the one feature I am looking for from within fluxbox is missing in openbox, so this is not an option.

Does anyone have a solution to any of the following?

1) Getting metacity (or whatever the default wm is) to tabulate new xterms by default via some setting
2) Getting fluxbox to run as the window manager for gnome desktop in 14.04.
3) A drop in replacement terminal that behaves like xterm that clusterssh can use as its terminal that has tabulation by default.  Remember, "terminator" and "konsole" don't work here...
4) A process similar to clusterssh that will open multiple interactive sessions in one command but do it in a tabbed window fashion (NOT me opening tabs myself to ssh to each server manually and then tying all of the tabs to one command input like terminator/konsole can do... that defeats the point of cssh)

I'll keep researching this on my own, but if anyone else has had any luck with any of the above, I'm very interested in the results and procedure you followed!

---

### Post by kc8hr on 2014-09-17
Here is one solution to your question: [http://ubuntuforums.org/showthread.php?t=63734](http://ubuntuforums.org/showthread.php?t=63734)

---

