---
title: "'s' key invokes shutdown menu when connected to Gnome desktop using VNC"
date: 2010-07-19
forum: Desktop Environments
---

### Post by ptipper on 2010-07-19
I've been trying to connect remotely to the Gnome desktop on Ubuntu 10.04 using VNC server and the TightVNC client on my Windows XP laptop. Everything appears to be working and displaying correctly, but for one show-stopping problem: when I type the 's' key on the keyboard, the Shutdown menu is invoked from the toolbar at the top of the Gnome desktop, even though I haven't held down the Ctrl or Alt keys. Similarly, if I type the 'm' key, the e-mail menu pops down from the tool bar. Both of these keyboard mis-mappings make the Gnome desktop effectively unusable when connected over VNC. Everything works correctly when connected directly using the server's local keyboard and monitor. I've spent hours searching for a solution, but I haven't managed to find a solution yet. I've also tried tweaking the settings of ~/.vnc/xstartup, so far to no avail, but here are the current contents of my xstartup file:

```
#!/bin/sh

# Uncomment the following two lines for normal desktop:
unset SESSION_MANAGER
# exec /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
## x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
## x-window-manager &
xterm -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
gnome-session &
# twm &

```We've also tried using another VNC client, i.e. UltraVNC, but we get exactly the same problem, so presumably the problem lies at the server end. Can anyone suggest how to prevent the shutdown and email menus from being incorrectly invoked when the 's' and 'm' keys are pressed?

---

### Post by rasheid2kx on 2011-01-04
i have this same exact problem running ubuntu 10.04.1 on a toshiba satalite 1005 s157. just doing regular stuff like browsing the the keys stop typing and start pulling menus.
did you slove your problem?

---

