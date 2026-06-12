---
title: "gdm not restartable without reboot"
date: 2005-12-03
forum: Desktop Environments
---

### Post by coldrick on 2005-12-03
Running Breezy on a Dell Inspiron 9300, which has an Nvidia card. Lately I've been having trouble restarting gdm, in particular because I need to use a separate monitor (a projector) as a screen clone. 

When I try to restart gdm (whether by Ctrl-Alt-Backspace or explicitly), I get sent to a command line (Ctrl-Alt-F1) which does *not* restart gdm, so I have to reboot.

On the advice of another thread I can re-install gdm, and that fixes the problem, but it reappears after a few changes to and from TwinView on and off.

Anyone seen this? Any suggestions re a workaround? And while we're at it, it sure would be nice - in Dapper, say - if Ctrl-Fn-F8 actually toggles btwn twinview-clone and not, so's we can catch up to the windoze folks.

Regards,
David

---

### Post by cwaldbieser on 2005-12-04
[QUOTE=coldrick]Running Breezy on a Dell Inspiron 9300, which has an Nvidia card. Lately I've been having trouble restarting gdm, in particular because I need to use a separate monitor (a projector) as a screen clone. 

When I try to restart gdm (whether by Ctrl-Alt-Backspace or explicitly), I get sent to a command line (Ctrl-Alt-F1) which does *not* restart gdm, so I have to reboot.

On the advice of another thread I can re-install gdm, and that fixes the problem, but it reappears after a few changes to and from TwinView on and off.

Anyone seen this? Any suggestions re a workaround? And while we're at it, it sure would be nice - in Dapper, say - if Ctrl-Fn-F8 actually toggles btwn twinview-clone and not, so's we can catch up to the windoze folks.

Regards,
David[/QUOTE]

If X doesn't restart, you can manually restart it with
```

$ startx

```
You can go straight to your Gnome desktop with
```

$ gnome-session

```

If you want to start gdm again, I think you need rootly powers, so you might need to:
```

$ sudo /usr/sbin/gdm

```
Not sure if that last one is right because I have never tried it.

---

### Post by Rob2687 on 2005-12-04
sudo /etc/init.d/gdm restart

seems to work for me.

---

### Post by magnusbb on 2005-12-04
I had the same problem a while a go, but it seems to have gone away - i don't know why. I've upgraded the drivers from my ATI card since then - maybe that was the problem.

But here is the work-around I use while I had the problem. Just put this in your .bashrc file or whatever shell you're using (as posted earlier):

alias startgdm="sudo /etc/init.d/gdm restart"

Now at the prompt, login as your regular user and type **startgdm** when the problem occurs. That is a little (just a little) bit quicker.

---

### Post by coldrick on 2005-12-05
I guess I wasn't clear in my initial post: the problem is that restarting gdm (for example, by sudo /etc/init.d/gdm restart), doesn't.

If I'm in Gnome already, it simply takes me to console mode (like Ctrl-F1), but does *not* restart Gnome - I then have to log in, do a sudo reboot, and the system comes up ok.

Regards,
David

---

### Post by cwaldbieser on 2005-12-05
[QUOTE=coldrick]I guess I wasn't clear in my initial post: the problem is that restarting gdm (for example, by sudo /etc/init.d/gdm restart), doesn't.

If I'm in Gnome already, it simply takes me to console mode (like Ctrl-F1), but does *not* restart Gnome - I then have to log in, do a sudo reboot, and the system comes up ok.

Regards,
David[/QUOTE]
Does startx at least restart the X display server?  Or does that bomb out, too?  What happens when you try to start gdm?  Do you get any errors?

---

### Post by Moobert on 2006-04-30
I ran into this problem today on a dapper beta 2 install. Turns out xorg was trying to load a rather old xorg.conf found in my home directory, instead of the one in /etc/X11/.

---

