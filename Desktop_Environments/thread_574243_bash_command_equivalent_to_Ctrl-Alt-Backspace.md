---
title: "bash command equivalent to Ctrl-Alt-Backspace"
date: 2007-10-12
forum: Desktop Environments
---

### Post by RyanGT on 2007-10-12
I wrote a script to help me use my laptop in the classroom.  It basically copies an xorg.conf.projector file that runs the projector using Twinview clone to the xorg.conf.  Once the script runs, I need to restart X with Ctrl-Alt-backspace.  Is there a way to restart X from the script?

Thanks,

Ryan

---

### Post by eurgain on 2007-10-12
If you want to restart the graphical system, then

$ sudo /etc/init.d/gdm restart

should work.  (Change gdm to kdm if necessary.)

If you just want to kill the X server, which probably more accurately reflects Ctrl-Alt-Backspace then

$ sudo kill `cat  /tmp/.X0-lock`

will kill the server on the first display, since that file in /tmp contains just the pid of the first X server.  (Change 0 to a larger number if you have more than one X server.)

You may have to add some  NOPASSWD entries to /etc/sudoers if you want this to work without having to enter a password.

HTH
A

PS  If anyone can tell me why the X server does not store its pid in a file under /var/run, I'd really like to know!

---

### Post by RyanGT on 2007-10-12
The sudo kill `cat  /tmp/.X0-lock` command kills X, but does not restart it.  I tried adding startx to my script, but it doesn't work.  So, right now the script stops X, but I need to manually restart it.

This is my current script:

#!/bin/bash
sudo cp /etc/X11/xorg.conf.projector /etc/X11/xorg.conf
cp ~/.ipython/ipythonrc.class ~/.ipython/ipythonrc
sudo kill `cat  /tmp/.X0-lock`
startx

I would like it to make my changes and automatically stop and restart x in one clean shot.  Can this work?

Thanks,

Ryan

---

### Post by eurgain on 2007-10-12
OK, let's go through this..

I understand:

sudo cp /etc/X11/xorg.conf.projector /etc/X11/xorg.conf

stamping on your config, but

 cp ~/.ipython/ipythonrc.class ~/.ipython/ipythonrc

I don't know what you are doing!

sudo kill `cat /tmp/.X0-lock`

so, X r.i.p., fine...

startx

Don't think that will work, because the chances are that the script above was running as a child of an X server/or X session that was killed by the sudo kill... RIP and slayed all its children in the process, including the one that was running the script either before the startx or after (but it would be a slayed descendent anyway, so no show).

I see the problem - how to start a one X session from another of a different type.  Don't know the answer.  I'll think about it!

Sorry, not HTH
A

---

### Post by eurgain on 2007-10-12
Thunked...

OK. This is not an answer, but a way in to crack the problem.  Multiple parallel X sessions, like having multiple graphical logins...

What you are looking for is a way to have two X servers with different configurations between which you want to switch.  I think.

Well, this is sort of built in, with the fast user switcher.  I think, this is easier with KDE/KDM than Gnome/GDM (maybe because it has been around longer with K), but the same principles apply.

First, you have to figure out how to set up a new G/KDM session that uses your projector profile.  That is the hard part.

At the start of your class, log in as your desktop.  Then ask to switch user, and log in as the same user, but using the projector profile's session.  You then should have two X servers on two VTs.

Assuming all else to be equal, you should then be able to switch backwards and fowwards between the two using CTRL-ALT-F*n*, where *n* is probably 7 for the first session, and *n* is some number greater than 7 (but h.t.g. less than 13:-) for the second session.

That is just a skeleton solution, but put some flesh on the bones, and I think it will probably work!

HTH
A

---

