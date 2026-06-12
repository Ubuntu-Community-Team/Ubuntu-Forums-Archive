---
title: "Metacity Crashes - Ubuntu 12.04"
date: 2015-01-19
forum: Desktop Environments
---

### Post by iPelle on 2015-01-19
Hi,

I'm running Ubuntu 12.04 (Gnome 3) on a Dedicated Server. To control remotely I use x2go, but about a week ago Metacity start crashing.

If I run it "manually" using the command
```
metacity --replace
```
it start but after about a minute it crashes again, returning the message:
```
[xcb] Extra reply data still left in queue
[xcb] This is most likely caused by a broken X extension library
[xcb] Aborting, sorry about that.
metacity: ../../src/xcb_io.c:576: _XReply: Assertion `!xcb_xlib_extra_reply_data_left' failed.
Aborted (core dumped)
```

How can I solve that?

Thanks.

P.S. Sorry for my bad english.

---

### Post by Frogs Hair on 2015-01-19
Hello and Welcome

If a Metacity session is installed login to that session at boot rather than use the command . Since Gnome 3 was released the command doesn't work as it did in Gnome 2. Edit: If you are logging into Metacity you will need to wait for a user running a similar setup for advice. Metacity is low resource and should be stable if the hardware is sufficient to run it.

---

### Post by iPelle on 2015-01-19
Thanks,

I can't access to the login screen. In x2go I access directly to the user account.

I can use a custom command to connect. Is there a command that "force" metacity at login?

---

### Post by Frogs Hair on 2015-01-19
There are threads with instructions to change the default session from Ubuntu to another installed session, in other words, the computer would boot into the Metacity session. . Make sure any instructions are relevant to 12.04 but, I don't know anything about doing that remotely though.

---

