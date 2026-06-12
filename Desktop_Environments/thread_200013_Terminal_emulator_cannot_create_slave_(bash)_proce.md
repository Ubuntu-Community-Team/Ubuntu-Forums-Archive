---
title: "Terminal emulator cannot create slave (bash) process"
date: 2006-06-19
forum: Desktop Environments
---

### Post by superbiskit on 2006-06-19
My last try here was so good, I have to try again.

Any attempt to launch a terminal emulator results in an error box:
"There was an error creating the child process for this terminal"

Likewise, gksu appears unable to start anything.

HOWEVER, emacs shell mode is quite happy to do
$ sudo emacs . . .
and create a second window running as root.

Having two emacsen running, however is a bit of overkill for the sort of things I usually want to do.

Could some kind soul suggest what I may have broken to get in this mess, or in the alternative, how I can track down the problem.  Because the error message just says "an error", and other functions simply fail silently, I'm not quite sure what is impossible.  I would expect an inability to spawn would cause much much more serious problems, besides which emacs is obviously spawning the second copy via sudo.  In fact, emacs has spawned bash (on a pty I think), bash has spawned sudo, and sudo has probably spawned the second emacs.  So that's probably not the problem.  Maybe something to do with passing X credentials around?
Anyway, I'm rather at a loss.

---

### Post by gnack on 2006-06-19
> My last try here was so good, I have to try again.

Any attempt to launch a terminal emulator results in an error box:
"There was an error creating the child process for this terminal"

I'm assuming you mean a terminal like gnome terminal or rxvt - how are
you trying to launch it (via the command line or the application menu)?

> Likewise, gksu appears unable to start anything.

What's the command you're trying?

> 
Could some kind soul suggest what I may have broken to get in this mess, or in the alternative, how I can track down the problem.  Because the error message just says "an error", and other functions simply fail silently, I'm not quite sure what is impossible.  I would expect an inability to spawn would cause much much more serious problems, besides which emacs is obviously spawning the second copy via sudo.  In fact, emacs has spawned bash (on a pty I think), bash has spawned sudo, and sudo has probably spawned the second emacs.  So that's probably not the problem.  Maybe something to do with passing X credentials around?
Anyway, I'm rather at a loss.

Can you run whatever you're trying to run with sudo?

---

### Post by superbiskit on 2006-06-19
[QUOTE=gnack]I'm assuming you mean a terminal like gnome terminal or rxvt - how are
you trying to launch it (via the command line or the application menu)?
[/QUOTE]
I've tried both ways, with both of those terminals.  gnome-terminal gives the stated error box, rxvt just sits like a dummy and does nothing (no prompt).



[QUOTE=gnack]What's the command you're trying?[/QUOTE]
It varies.  This applies to every command I've tried.



[QUOTE=gnack]Can you run whatever you're trying to run with sudo?[/QUOTE]
From emacs shell mode, yes.  From the panel command line, no.

Anyway, I cannot get gnome-terminal to initiate the shell even for myself.

---

### Post by gnack on 2006-06-26
> I've tried both ways, with both of those terminals.  gnome-terminal gives the stated error box, rxvt just sits like a dummy and does nothing (no prompt).

It varies.  This applies to every command I've tried.

If you haven't solved this problem already, I'd recommend looking at your .profile
and .bashrc to see if something is trying to run but failing.  Rename your copies
and try to launch a gnome-terminal.

A google search indicates this message also might happen when there's a problem with udev (the 2.6 kernel /dev manager).   It doesn't offer much help for fixing the issue but please take a look at the info.

Also, try to log into one of the non-X terminal windows (i.e. cntrl-alt-F1) to test whether there's some Xorg/gnome issue.

Anyway, just some ideas.

---

### Post by superbiskit on 2006-06-27
[QUOTE=gnack]If you haven't solved this problem already, I'd recommend looking at your .profile
and .bashrc to see if something is trying to run but failing.  Rename your copies
and try to launch a gnome-terminal.
[/QUOTE]
Worth a try.  No, I haven't solved it.  If all else fails, my "Dapper" CD should be along soon, I hope.
[QUOTE=gnack]
A google search indicates this message also might happen when there's a problem with udev (the 2.6 kernel /dev manager).   It doesn't offer much help for fixing the issue but please take a look at the info.
[/QUOTE]
Sounds like the right track.  What did you search for?  I will take a look at the udev documents, anyway.
[QUOTE=gnack]
Also, try to log into one of the non-X terminal windows (i.e. cntrl-alt-F1) to test whether there's some Xorg/gnome issue.
[/QUOTE]
Did that.  Logs in with no problem.

And, thanks!

---

### Post by superbiskit on 2006-06-27
Your suggestion about udev did the trick!  Well, not directly, but reading the udev documents I found udev to be a successor of devfsd -- which I've been running.

Uninstalling devfsd allows my gnome-terminal to run correctly.

And again, thanks!

---

