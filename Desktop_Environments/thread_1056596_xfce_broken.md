---
title: "xfce broken :/"
date: 2009-01-31
forum: Desktop Environments
---

### Post by areka on 2009-01-31
Hello there !

I can't login in xfce, it says me that session lasted less than 10 seconds and display this error message :

```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
/usr/bin/startxfce4: X server already running on display :0
Agent pid 5845
** Message: Querying XINPUT extension
** Message: XINPUT extension found
** Message: Querying Xkb extension
** Message: Xkb extension found
** Message: Querying XF86Misc extension
** Message: XF86Misc extension found
** Message: Querying Xkb extension
** Message: Xkb extension found
** Message: another SSH agent is running at: /tmp/ssh-RKJDim5844/agent.5844
Connection failure: Connection refused

(xfce4-session:5847): libxfce4util-CRITICAL **: Failed to parse file /etc/xdg/autostart/eeepc-statusicon.desktop, ignoring.

(xfce4-session:5847): GLib-CRITICAL **: g_string_chunk_insert: assertion `chunk != NULL' failed

(xfce4-session:5847): GLib-CRITICAL **: g_string_chunk_insert: assertion `chunk != NULL' failed
Segmentation fault
Agent pid 5845 killed
```

Can someone help me please ?
Thanks !

Vince.

---

### Post by k3rnelmustard on 2009-01-31
Well, it says that X is already running... Is this happening on a clean boot?  Check Ctrl-Alt-F7 through F12 regardless and make sure xfce isn't sitting in one of those spots.  Otherwise, I would run a full system update ASAP!  I believe it's (from a terminal: Ctrl-Alt-F1 through F6)
```

sudo apt-get -u upgrade

```

It seems you may have some kind of version mismatch between glib and xfce4.  If this isn't the command, it's similar, look around a bit.

---

