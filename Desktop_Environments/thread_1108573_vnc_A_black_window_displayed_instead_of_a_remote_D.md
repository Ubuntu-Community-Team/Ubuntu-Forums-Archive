---
title: "vnc: A black window displayed instead of a remote Desktop"
date: 2009-03-27
forum: Desktop Environments
---

### Post by juliosergio on 2009-03-27
Hello,

[LEFT]I'm intending to use vnc to view a remote desktop from a RedHat server in an Ubuntu Work Station (WS). As my first alternative was the software the machines already have, I'm using "vncserver" and "vncviewer" produced by realvnc, I think. When I used that combination (i.e., vncserver / vncviewer) for the first time, the Ubuntu WS nicely displayed the
RedHat Server Desktop. After several tries, however, the WS isn't displaying the Desktop anymore: the only thing I get now is a black (or grey)  window with an "X" cursor that moves as I move the mouse.
[/LEFT]
The details of the problem are as follows:

I started a vncserver in a RedHat Server with:
[INDENT]     vncserver :11 -geometry 1000x700[/INDENT]

The RedHat Server responded with
[INDENT]    xauth: (stdin):1:  bad display name "elcaos.imta.mx:11" in "add" command
    New 'elcaos.imta.mx:11 (checo)' desktop is elcaos.imta.mx:11
    Starting applications specified in /home/checo/.vnc/xstartup
[/INDENT]
The content of the xstartup file is:

[INDENT]    #!/bin/sh

    # Uncomment the following two lines for normal desktop:
    unset SESSION_MANAGER
    export DESKTOP="GNOME"
    exec /etc/X11/xinit/xinitrc
[/INDENT]
When I run the vnc client (vncviewer) in my Ubuntu Work Station the only thing I get is a black window, with an "X" cursor that moves as I move the mouse. The thing is that in the beginning the pair (vncserver / vncviewer) worked pretty well but now is just displaying this weird window.

Do you have any idea on what's happening?

Thanks

Sergio.

---

