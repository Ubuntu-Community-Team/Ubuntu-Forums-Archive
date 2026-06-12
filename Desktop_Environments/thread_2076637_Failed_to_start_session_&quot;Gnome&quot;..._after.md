---
title: "Failed to start session &quot;Gnome&quot;... after 12.10 upgrade"
date: 2012-10-26
forum: Desktop Environments
---

### Post by robothebobo on 2012-10-26
This is happening on an xubuntu computer that I don't access physically - I access it using ssh and very occasionally use the GUI via VNC (Xtightvnc).

Since upgrading from 12.04 to 12.10 (via ssh using 'do-release-upgrade'), I'm unable to use the GUI through VNC anymore. When I connect (first using the 'vncserver' command to launch an X server), I'm met with a grey screen and a single dialog box that says 'Failed to start session "Gnome"'. I can dismiss it, and then stare at a blank grey screen. Not much else.

I'm further puzzled because I thought Xfce was an alternative to Gnome, so I don't understand the message I'm getting... Any help appreciated.

---

### Post by Toz on 2012-10-26
Hello and welcome to the forums.

Sounds like you might have vnc setup to start a gnome session. Can you post back the host system's vnc startup file?

---

### Post by robothebobo on 2012-10-26
> **Toz said:**
> Hello and welcome to the forums.

Sounds like you might have vnc setup to start a gnome session. Can you post back the host system's vnc startup file?

Hi Toz,

This is what I have in my ~/.vnc/xstartup file:

```
#!/bin/sh

xrdb $HOME/.Xresources
xsetroot -solid grey
#x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
#x-window-manager &
# Fix to make GNOME work
export XKL_XMODMAP_DISABLE=1
/etc/X11/Xsession

```

I don't know if it's relevant, but I don't have a ~/.Xresources file.

---

### Post by Toz on 2012-10-26
Do you have a ~/.xsession, ~/.xsessionrc or ~/.Xsession file? If so, what are the contents?

You could try changing the last line to read:
```
startxfce4 &
```
...this should start Xfce directly.

---

### Post by robothebobo on 2012-10-26
> **Toz said:**
> Do you have a ~/.xsession, ~/.xsessionrc or ~/.Xsession file? If so, what are the contents?

You could try changing the last line to read:
```
startxfce4 &
```
...this should start Xfce directly.

Thank you! startxfce4 & got it working, although there are now errors given after I run 'vncserver': .Xauthority was owned by root:root with permissions 600, and vncserver gave an error message:

xauth:  /home/robo/.Xauthority not writable, changes will be ignored

After I changed ownership to robo:robo, I get this error, repeated twice:

xauth:  timeout in locking authority file /home/robo/.Xauthority

There are clearly a lot of things I need to learn about using this :)

---

