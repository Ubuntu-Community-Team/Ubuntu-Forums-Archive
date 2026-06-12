---
title: "Unable to run Synaptic  GTK-WARNING cannot open display"
date: 2013-04-19
forum: Desktop Environments
---

### Post by 316479 on 2013-04-19
I have an **intermittent  **problem trying to use Synaptic

**As an ordinary user:**

          Select  Applications Menu -> System -> Synaptic Package Manager.
          I get prompted for my password, but then nothing happens, Synaptic doesn't start up.

          The relevant piece of my /usr/share/applications/synaptic.desktop is
                        Exec=gksudo synaptic

Also a lock file    ~/.gksu.lock  gets left in my home directory.
No relevant messages in  ~/.xsession-errors  or in /var/log/Xorg.0.log

**&#8203;As root:**

         # synaptic 

         I get the error message

                No protocol specified
                (synaptic:3456)  Gtk WARNING: ** cannot open display:  :0.0

and synaptic doesn't run.

**None**&#8203; of the usual fixes  work

               ln -s /home/<real user>/.Xauthority  /root/.Xauthority
        or    export  XAUTHORITY=/home/<real user>/.Xauuthority
or xauth merge /home/<real user>/.Xauthority
        or    export  DISPLAY=:0.0

Curiously, rebooting usually solves this intermittent problem.
After a reboot I can run Synaptic as an ordinary user or as root.

---

