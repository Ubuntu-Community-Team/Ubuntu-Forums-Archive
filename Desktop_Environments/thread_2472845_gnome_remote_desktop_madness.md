---
title: "gnome remote desktop madness"
date: 2022-03-14
forum: Desktop Environments
---

### Post by drw06g0w7-frank on 2022-03-14
I have two 21.10 systems that can run both xorg.x11 and wayland environments. I'm going nuts with gnome remote desktop. The most obvious symptoms are awful performance, long key-press turnaround time, loss of CAPS-LOCK function and characters repeating after you quit typing. I haven't yet narrowed it down to see if wayland has to be involved or not. I definitely can reproduce the problem if at least one of the systems is wayland.

I noticed today that initially everything appeared to work as expected (well, almost. The caps-lock light was backwards.).

After exiting remote desktop locally, I have one remote desktop daemon running (as I would expect)

fbacher@smeagol:~$ ps -ef|fgrep -i remote
fbacher   244497  243975  0 07:04 ?        00:00:00 /usr/libexec/gnome-remote-desktop-daemon

I just noticed that I have multiple xdg desktop procsses (perhas this is normal?)
fbacher@smeagol:~$ ps -ef|fgrep xdg
fbacher   244282  243975  0 07:04 ?        00:00:00 /usr/libexec/xdg-permission-store
fbacher   247450  243975  0 08:08 ?        00:00:00 /usr/libexec/xdg-desktop-portal
fbacher   247454  243975  0 08:08 ?        00:00:00 /usr/libexec/xdg-document-portal
fbacher   247463  243975  0 08:08 ?        00:00:00 /usr/libexec/xdg-desktop-portal-gtk
root      253313  243975  0 08:57 ?        00:00:00 /usr/libexec/xdg-desktop-portal
root      253318  243975  0 08:57 ?        00:00:00 /usr/libexec/xdg-document-portal
root      253322  243975  0 08:57 ?        00:00:00 /usr/libexec/xdg-permission-store
root      253333  243975  0 08:57 ?        00:00:00 /usr/libexec/xdg-desktop-portal-gtk

I haven't yet figured out why there are multiple ones. systemctl --type=service has not yieled anything that catches my eye yet. I haven't yet figured out how to restart these. A search on the web hasn't shed any light yet either.

I would switch to another vnc server, but to my knowledge they don't yet exist on wayland.

---

### Post by TheFu on 2022-03-14
x2go worked with Wayland when I tested 21.04, but not with Gnome3+. There's something about Gnome after v2 that just breaks things. I was told last week that KDE-Plasma has similar issues, but I don't know about that myself.

For me, Wayland breaks a number of very important workflows, so it is DOA here except as a slightly interesting, incomplete, attempt to improve GUI performance and security until all the workflows have reasonable solutions.

We each need to pick our battles.

---

### Post by ActionParsnip on 2022-03-15
What are you doing on the remote system that needs the full desktop session? There may be a sleeker solution to what you want to achieve

---

### Post by him610 on 2022-03-16
Using *x2go* on a machine with Xubuntu 20.04.4 is a non-issue.

---

