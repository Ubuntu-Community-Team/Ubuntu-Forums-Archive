---
title: "vncserver shows ugly window manager"
date: 2013-10-24
forum: Desktop Environments
---

### Post by TDdGk7A on 2013-10-24
For some inexplicable reason I never manage to get exactly the same desktop when I login into a vncserver session compared to when I log in normally. Every new version of xubuntu I try and then I give up again.

I am running xubuntu 13.10, vnc4server, and the following .vnc/xstartup:

```
#!/bin/sh


# Uncomment the following two lines for normal desktop:
# unset SESSION_MANAGER
# exec /etc/X11/xinit/xinitrc


[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
x-window-manager &
startxfce4 &

#xfce4-session &   # using this instead of startxfce does not help
#xfwm4&             # using the following three rows doesn't help
#xfdesktop4&
#xfce4-panel&

```

I think I've tried quite a lot of permutations of commenting and uncommenting lines in this file, all to no avail. The best I get is a 90's grey menu bar design. Because there don't seem to be any vnc server alternatives currently for 13.10, I was wondering if anybody got the correct XFCE desktop working with vnc4server?

---

