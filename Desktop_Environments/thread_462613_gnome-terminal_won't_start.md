---
title: "gnome-terminal won't start"
date: 2007-06-02
forum: Desktop Environments
---

### Post by Mantis2600 on 2007-06-02
I booted my system up, and now gnome-terminal doesn't start when I try to run it.  This is a fresh install with very few synaptic packages installed, so it's not the compiaz problem that I've seen in the forums.  Any ideas?

---

Ran Konsole and got this:

> The program 'gnome-terminal' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 105 error_code 2 request_code 78 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)


---

### Post by rusty0101 on 2007-06-05
Running into the same problem.

even doing 'sudo apt-get install --reinstall gnome-terminal' does nothing for me. Still get the following text when attempting to run gnome-terminal from an xterm:

```

:~$ gnome-terminal
The program 'gnome-terminal' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 105 error_code 2 request_code 78 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

---

### Post by rusty0101 on 2007-06-07
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/58232](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/58232) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Not seeing a lot of responses here, I haven't tested the workaround yet, but in bug 58232 it appears that there is a bug in the nvidia proprietary drivers that shows up when ximera and compositing are both enabled.

---

### Post by rusty0101 on 2007-06-07
OK, for me the workaround is working. so I think my issue is directly related to the bug. Also have a minor issue with the gnome-wm not being live when I start X, which I used to be able to fix by kicking off "desktop effects" then when that 'failed' it would automatically launch gnome-wm. My current fix is to launch that from a gnome-terminal session.

I suspect that the reason that gnome-wm is not launching properly is that for some reason the first time I select any of the exit options from the 'Quit' menu a couple of windows may close, but nothing else happens. I don't see any dialogs asking me if I want to save documents, etc. This has been a minor annoyance for some time though, so I have doubts that it is related to the bug with gnome-terminal

-Rusty

---

