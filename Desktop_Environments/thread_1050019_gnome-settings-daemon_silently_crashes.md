---
title: "gnome-settings-daemon silently crashes"
date: 2009-01-25
forum: Desktop Environments
---

### Post by Mr. Big on 2009-01-25
Hi!
I'm running ubuntu-intrepid, everything is up-to-date. Since a while ago sometimes (about 1 of 5) when I log in gnome-settings-daemon does not start. Nothing notifies me about this, but the wrong themes is loaded.

I've started g-s-d with --no-daemon --sync --debug, and got the following error:
The program 'gnome-settings-daemon' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 1251 error_code 8 request_code 20 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
[1232883978,000,xklavier.c:xkl_engine_start_listen/]    The backend does not require manual layout management - but it is provided by the applicationxrdb:  "*Label.background" on line 220 overrides entry on line 150
xrdb:  "*Text.background" on line 226 overrides entry on line 191
xrdb:  "*Label.foreground" on line 232 overrides entry on line 151
xrdb:  "*Text.foreground" on line 238 overrides entry on line 192

I've got two laptopts, mostly same hardware running same ubuntu versions, and I've noticed this on both.

Could not find anything on the net yet, what describes my problem the closest is this: [https://bugzilla.redhat.com/show_bug.cgi?id=466206](https://bugzilla.redhat.com/show_bug.cgi?id=466206) - expect I don't have those packages installed.

Any ideas?

---

### Post by vipseixas on 2009-01-25
My g-s-d crashed a lot when I used Ubuntu 64 bits (3 times a day), since I changed to Ubuntu 32 bits it stopped crashing all the times (only 2 times in 3 months). It usually crashed when I was using Firefox.

---

### Post by Mr. Big on 2009-01-25
I'm running 64bit, but this crash only happens during login. I didn't notice it during work. It seems very likely that it conflicts with something that does start at the same time.
Btw, I have only the default applets running: battery, networkmanager, sound mixer and the date/time applet.

---

