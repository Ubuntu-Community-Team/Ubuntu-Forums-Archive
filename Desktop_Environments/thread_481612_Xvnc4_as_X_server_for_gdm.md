---
title: "Xvnc4 as X server for gdm"
date: 2007-06-22
forum: Desktop Environments
---

### Post by eremos on 2007-06-22
Hi guys,

I know there is plenty of information about running Xvnc4 through xinetd, but I'm trying to set it up directly through gdm.

Here's what I had for VNC server 3, which worked very well:

```

[servers]
0=Xvnc3

[server-Xvnc3]
name=Xvnc3 Server
command=/usr/bin/Xvnc  -geometry 1024x640 -depth 24 -desktop hq -NeverShared
```

I tried switching to VNC4 because of [this bug](https://bugs.launchpad.net/bugs/108928), using this configuration:

```
[servers]
0=Xvnc4

[server-Xvnc4]
name=Xvnc4 Server
command=/usr/bin/Xvnc -geometry 1024x640 -depth 24 -desktop hq -NeverShared -SecurityTypes None -fp /usr/share/X11/fonts/misc/
```

But when I log in all I get is the grey screen with the X for a cursor.

If I enable automatic log in gdm.conf the X session "lasts less than 10 seconds" with the following appearing in .xsession-errors:

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "elmarie"
/etc/gdm/Xsession: Beginning session setup...
The program 'x-session-manager' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadRequest (invalid request code or no such operation)'.
  (Details: serial 74 error_code 1 request_code 146 minor_code 2)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

Is this a bug or is there something I can configure to make this work?

Thanks in advance

Edit: Found solution at [https://bugs.launchpad.net/ubuntu/+source/vnc4/+bug/110263](https://bugs.launchpad.net/ubuntu/+source/vnc4/+bug/110263)

Had to add -extension XFIXES to VNC command line to disable that extension (which was mistakenly being advertised by VNC as being supported).

---

