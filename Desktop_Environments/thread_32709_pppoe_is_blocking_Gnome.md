---
title: "pppoe is blocking Gnome"
date: 2005-05-09
forum: Desktop Environments
---

### Post by [Malte] on 2005-05-09
This may be the same issue as in the "Gnome startup" thread; however, I didn't figure out how to solve it.

On Saturday I installed the 'Hoary Hedgehog' - a breeze. Everything is just working. Nearly everything.

I cannot start Gnome when pppoe, which is maintaining an ADSL connection, is up. If I call "sudo poff", then Gnome will be able to start, and calling "sudo pon" after that works, too. But that's too tedious a procedure if you have to do it every time you start your computer.

What is actually happening? I log into gdm (or I call startx from a console), and X starts correctly, but Gnome does not. The output of ps is the following:

```
  PID TTY          TIME CMD
 6949 tty1     00:00:00 bash
 7402 ?        00:00:00 gnome-session
 7452 ?        00:00:00 ssh-agent
 7455 ?        00:00:00 dbus-daemon-1
 7456 ?        00:00:00 dbus-launch
 7458 ?        00:00:00 gconfd-2
 7461 ?        00:00:00 gnome-keyring-d
 7499 tty1     00:00:00 ps
```

Obviously there are a number of Gnome processes missing. .xsession-errors is:

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "malte"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/krokodilo:/tmp/.ICE-unix/7402
```

Or, when started by startx instead of gdm:

```
Xsession: X session started for malte at Mo Mai  9 11:28:18 CEST 2005
SESSION_MANAGER=local/krokodilo:/tmp/.ICE-unix/8668
```

Any hints?

---

### Post by [Malte] on 2005-05-10
Sorry for the noise, but hasn't anyone a idea what is going on here?

---

### Post by [Malte] on 2005-05-13
So very well - this bug had already been reported. For anyone interested, it's bug #9136 ([https://bugzilla.ubuntu.com/show_bug.cgi?id=9136)](https://bugzilla.ubuntu.com/show_bug.cgi?id=9136)).

---

