---
title: "autostarting a terminal window in Unity"
date: 2018-07-20
forum: Desktop Environments
---

### Post by Skaperen on 2018-07-20
i tried autostarting a terminal under Unity with a file ~/.config/autostart/terminal.desktop containing:

```
[Desktop Entry]
Type=Application
Name=Terminal
Exec=gnome-terminal
Icon=<gnome-terminal
Comment="I hope this works"
X-GNOME-Autostart-enabled=true
```

when i logged out and logged back in a terminal window was started, but it was started at position 0,0 (hard upper left) and both the left side and top window header decoration were underneath Unity stuff such as the panel of buttons on the left.  it appears as if the terminal window came up before the Unity stuff did.  it was started quite earlu.

so i modified this file to run my own script to sleep 10 seconds then start a few terminals.  the script works fine when run manually. however when logging out logging back in and waiting at least 20 seconds nothing happened beyond Unity starting up normally.  there were commands in the script to touch and output to various files in /tmp.  none of them showed up.  basically the script did not get run.  here is the new desktop file with only the  Exec line changed:

```
[Desktop Entry]
Type=Application
Name=Terminal
Exec=/home2/ka9wgn/9terms
Icon=<gnome-terminal
Comment="I hope this works"
X-GNOME-Autostart-enabled=true
```

so, how can i make this one run?  my script had lines like this that worked when run manually but not when i had referenced by that terminal.desktop file.

```
exec 1>/tmp/9terms.out
exec 2>/tmp/9terms.err
touch /tmp/1
sleep 10
touch /tmp/2
```

are private scripts not allowed by Unity?

---

### Post by mc4man on 2018-07-20
Try adding your delay to the autostart .desktop, i.e (where X = seconds, 3 or so should suffice
X-GNOME-Autostart-Delay=X

---

### Post by Skaperen on 2018-07-20
the delay works, now, but the window is still placed at the hard top and the title bar of the terminal window under the Unity top panel. it does, now, get placed to the right of the vertical row of larger square buttons.  when i start the terminal manually, it gets placed below that bar at the top.  i increased the delay to 15 seconds but that made no difference.

---

### Post by mc4man on 2018-07-20
Can't duplicate your problem about placement, opens as expected if nothing is already open. 
If inclined set up another user, give them the autostart .desktop, I'd bet it works fine there..

---

### Post by Skaperen on 2018-07-20
i found the discrepancy.  the misplacement happens when the terminal window opens while the display is switched to a different X server than the one running for the user where Unity is initializing for a fresh login and later opening the terminal window.  this is caused by my automated setup which logs in the 12 usernames i use, switching through them faster than they can initialize.  until this, it all worked well.  now i need to increase the time delay between users.

---

