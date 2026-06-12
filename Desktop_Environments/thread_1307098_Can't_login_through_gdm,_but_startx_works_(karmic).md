---
title: "Can't login through gdm, but startx works (karmic)"
date: 2009-10-30
forum: Desktop Environments
---

### Post by gward on 2009-10-30
I first installed karmic Xubuntu around alpha 4, and back then I was able to login via gdm: it started my XFCE session no problem.  But for several weeks now, login via gdm has failed.  It spins for a few seconds and then goes back to the user selection screen.

/var/log/daemon.log hints at the problem:

```

Oct 30 21:14:19 gollum gnome-session[3840]: devkit-power-gobject-WARNING: Couldn't enumerate devices: The name org.freedesktop.DeviceKit.Power was not provided by any .service files
Oct 30 21:14:19 gollum gnome-session[3840]: WARNING: Could not launch application 'metacity.desktop': Unable to start application: Failed to execute child process "metacity" (No such file or directory)
Oct 30 21:14:20 gollum gnome-session[3840]: WARNING: Could not launch application 'gnome-power-manager.desktop': Unable to start application: Failed to execute child process "gnome-power-manager" (No such file or directory)

```

Huh?  Why is gdm running gnome-session under Xubuntu?  

If I login on the console and then run startx, it's fine: that starts up my XFCE session as expected.

---

### Post by gward on 2009-10-30
Forgot to mention: while this was a clean OS install, I'm using the same home directory that I've been carrying around for ~12 years.  So there is some history there.  Most recently, I used it with GNOME under intrepid and jaunty.  

Hypothesis: something in my home directory is making gdm run gnome-session, which then fails.

Confirmation: I created a test user with a barebones home directory.  Can login just fine via gdm as the test user.

Hmmmm.  Now I just have to whittle down what's in my home directory that is screwing up gdm.

---

### Post by lidex on 2009-12-29
Look in "/home/username/.config/autostart" (username=your user name) and delete "metacity.desktop" and "gnome-power-manager.desktop"



> Hmmmm. Now I just have to whittle down what's in my home directory that is screwing up gdm.
Run this command in terminal:
```
locate gnome-session
```

---

