---
title: "GDM: not enough ptys"
date: 2007-08-15
forum: Desktop Environments
---

### Post by B-Con on 2007-08-15
I couldn't log in to Ubuntu last time I tried. It booted fine, got to the login screen, but when I attempted to log in to anything -- XClient, Gnome, Fluxbox -- I got a screen with what looks like a Gnome Terminal and an error box saying:
> There was an error creating the child process for this terminal
I'm not sure *why* it's trying to create a terminal in the first place, I have nothing like that in any startup scripts. I can close the error box, but after that I can't do anything except go back to the login by using Ctrl+Alt+Backspace. 

However, when I tried to log into a Failsafe Terminal I get the following error:
> /etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "b-con"
xterm: Error 32, errno 2: No such file or directory
Reason: get_pty: not enough ptys

I've never had a problem like this before and on my last bootup I didn't change a thing, especially not anything GDM related.

A simple reboot fixed the problem, but I don't like this.

As an aside, might this be related to BusyBox? I randomly (maybe 1 out of 10 times) get a BusyBox error on bootup that I see is apparently common to debian-based distros, but I haven't bothered to fix it because it just started, I'm lazy, and it's so infrequent it doesn't bother me. Between this problem and BusyBox, I now have two problems that randomly prevent me from starting Ubuntu. This is starting to get obnoxious.

Any solutions?

---

### Post by MikeL123 on 2007-09-15
Hi B-Con,

I have the same problem. However, a simple reboot did not fix my problem.

I never had this problem before.

What happened was:
1. I hibernate my laptop.
2. Removed my laptop from Dock.
3. Resumed without Dock.
4. Got a blank screen when X started. (Probably my x setting putting image into external monitor.)
5. Then I pressed power button to shutdown my laptop.
6. Restart my laptop in dock.
7. Then the problem as described by B-Con started.

In addition, when I tried to login via terminal, I get a bash error
"/dev/null : permission denied"

any help is much appreciated.

---

