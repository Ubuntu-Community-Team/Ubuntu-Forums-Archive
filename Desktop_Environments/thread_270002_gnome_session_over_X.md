---
title: "gnome session over X"
date: 2006-10-02
forum: Desktop Environments
---

### Post by jhefferon on 2006-10-02
Hello,

I am switching over from a RedHat laptop to Ubuntu.  I'm having a problem with a proceedure that worked on the older laptop.  I'd be very grateful for any suggestions.

I want to connect to a remote server.  I get a new command line with <ctl>-<alt>-F2.  I log in.  I say "xinit -- :1" and that brings up an X screen with an open terminal.  I click into the terminal and "ssh -C [email]myname@my.distant.mach[/email]ine".  I log into that server.

Now on that server I run "gnome-session".  On my old box there was a pause and eventually I got a look at my distant desktop, as though I had logged in from its keyboard (but on my laptop it lives at <ctl>-<alt>-F8)  Here, I just get an error message: Gtk WARNING **: cannot open display: .

I have "X11Forwarding yes" in my sshd_config locally (that is, on the machine whose keyboard I am at).  I also have "X11DisplayOffset 10" and "X11UseLocalhost no" (for this latter I've tried yes, no and delete).  I am careful to restart the sshd each time I make a change.

I can see no messages in any log files, although I admit to not being too sure which log files to look at.

The remote machine is old enough that it does not use an X.org version of X, if that matters (Debian Sarge).

Again, I can run these commands from another laptop and they work, so I suspect something with the Ubuntu setup, but I am a bit stuck.  Anyone have any ideas?

Thank you,
Jim

---

### Post by jhefferon on 2006-10-11
Sorry to reply to my own message but I figured it out and I thought that I'd list the answer.

> **jhefferon said:**
> Hello,

I want to connect to a remote server.  I get a new command line with <ctl>-<alt>-F2.  I log in.  I say "xinit -- :1" and that brings up an X screen with an open terminal.  I click into the terminal and "ssh -C [email]myname@my.distant.mach[/email]ine".  I log into that server.

Now on that server I run "gnome-session".  On my old box there was a pause and eventually I got a look at my distant desktop, as though I had logged in from its keyboard (but on my laptop it lives at <ctl>-<alt>-F8)  Here, I just get an error message: Gtk WARNING **: cannot open display: .



I needed to say "ssh -C -X [email]myname@remote.comp[/email]uter".  The -X forwards the DISPLAY variable (or something like that).

Jim

---

### Post by s_p_a_r_k_y on 2006-10-11
you can also turn on X11Forwarding yes in /etc/ssh/ssh_config *as well as sshd_config and then you don't need the -X flag

---

