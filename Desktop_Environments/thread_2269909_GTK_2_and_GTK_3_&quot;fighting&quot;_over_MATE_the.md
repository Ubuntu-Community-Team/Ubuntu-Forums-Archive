---
title: "GTK 2 and GTK 3 &quot;fighting&quot; over MATE theming"
date: 2015-03-18
forum: Desktop Environments
---

### Post by jwbrase on 2015-03-18
I am running an Ubuntu 14.04 setup with the Ubuntu-MATE repositories added after installation. My desktop setup includes MATE as my DE, Compiz as my WM, and Emerald as my window decorator.

On February 23rd, my system had been up almost 90 days since the last reboot. I launched a game on Steam that I know to have some graphical issues, and lost window decoration. I take this to be a result of Emerald crashing. I launched an alternate WM to get its window decorations so I could move windows around while I finished up what I was doing, then logged out of my session and logged back in. MATE hung at login and I have not since been able to successfully start a MATE session (I can log in to XFCE and twm. I eventually tried restoring my system from backup to the state as of the morning of the 23rd, before all of this started.

However, the restore did not solve the issue. This seems to indicate that MATE had ended up in an inconsistent state on disk at some unknown point in the past, but that my desktop session had continued running without trouble due to having been initially loaded from old binaries and configuration before the installation got borked on disk. Depending on when this occured, I may or may not have backups going back to that date, as my backup disk had failed and been replaced in the middle of the 90 day timeframe that the MATE session had been running.

The specific symptoms I have been experiencing, and continue to experience after the restore are as follows:

MATE is completely unresponsive to mouse input. mate-panel is displayed, and the panel, and all windows launched at login, flash between my custom GTK 2 theme and a default grey GTK 3 theme. When the GTK 3 theme is displayed, a gnome-terminal instance that is auto-launched on login displays the default Ubuntu purple-and-white terminal theme, which then flashes back to my terminal theme when the panel flashes back to GTK 2 theming (actually, the gnome-terminal bit I only recall seeing after the restore, but the rest is the same both before and after). gtk-window-decorator appears in the process list. The system monitor widgets for the panel are displayed, but do not display their graphs. On switching out to a console, top reports 100% CPU load on all four cores, with Xorg, Compiz, and mate-panel being among the processes displayed as using significant amounts of CPU.

I brought this issue up on the MATE forums, and it was suggested that I try creating a new user and logging into MATE with that user. In that case, MATE does respond to mouse input, but various components of the desktop session still put the CPU under full load on all four cores, and MATE still flashes between GTK 2 and GTK 3 theming. I have not been able to get any further advice on the issue at the MATE forums.

Can anyone provide any input on possible resolutions to this mess?

---

