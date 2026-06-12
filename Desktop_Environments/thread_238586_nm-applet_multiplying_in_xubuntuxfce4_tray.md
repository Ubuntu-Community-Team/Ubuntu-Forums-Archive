---
title: "nm-applet multiplying in xubuntu/xfce4 tray"
date: 2006-08-17
forum: Desktop Environments
---

### Post by nothsa on 2006-08-17
I installed NetworkManager withough any problems, but I keep getting more and more "nm-applet" processes starting up each time I restart my computer.

When I start my computer and log in, it (now) starts about 10 nm-applet processes and I have to manually remove 9 of them from the system tray (right-click > remove). If I reboot the computer and log in again, all 10 processes start up again, and sometimes it'll add another one.

I will be eternally grateful if anyone can tell me how to stop all these processes from spawning. I'm Linux savvy, so I'll try any suggestions you're willing to throw my way.

---

### Post by meng on 2006-08-17
I can't tell you why they're breeding like rabbits - but have a look in System > Preferences > Sessions > Startup Programs and see if there are multiple entries.
EDIT: Whoopsie, didn't read this properly, thought it was in GNOME. Sorry.

---

### Post by chickengirl on 2006-08-17
> **meng said:**
> I can't tell you why they're breeding like rabbits - but have a look in System > Preferences > Sessions > Startup Programs and see if there are multiple entries.
EDIT: Whoopsie, didn't read this properly, thought it was in GNOME. Sorry.
Try looking in Settings > Sessions and Startup Settings to see if there are multiple entries, then.

---

### Post by nothsa on 2006-08-17
> **chickengirl said:**
> Try looking in Settings > Sessions and Startup Settings to see if there are multiple entries, then.
There doesn't appear to be any program listings there. I have 2 tabs: "General" and "Advanced". Here is the break-down of my settings:

General
    [INDENT]Session Chooser
        [INDENT][ ] Display choose on login[/INDENT]
    Logout settings
        [INDENT][ ] Automatically save session on logout
        [x] prompt on logout
        [ ] Show hibernate button
        [ ] Show suspend button[/INDENT][/INDENT]
Advanced
    [INDENT]Compatability
        [INDENT][ ] Launch Gnome services on startup
        [ ] Launch KDE services on startup[/INDENT]
    Security
        [INDENT][ ] Manage remote applications[/INDENT][/INDENT]

---

### Post by chickengirl on 2006-08-18
> **nothsa said:**
> There doesn't appear to be any program listings there. I have 2 tabs: "General" and "Advanced". Here is the break-down of my settings:

General
    [INDENT]Session Chooser
        [INDENT][ ] Display choose on login[/INDENT]
    Logout settings
        [INDENT][ ] Automatically save session on logout
        [x] prompt on logout
        [ ] Show hibernate button
        [ ] Show suspend button[/INDENT][/INDENT]
Advanced
    [INDENT]Compatability
        [INDENT][ ] Launch Gnome services on startup
        [ ] Launch KDE services on startup[/INDENT]
    Security
        [INDENT][ ] Manage remote applications[/INDENT][/INDENT]

Oh, I'm sorry, that was the wrong one.

Try Settings > Autostarted Applications.

---

### Post by orb9220 on 2006-08-18
Nope I have looked and looked on this issue with no solution.

I have three always in the tray on startup and have to right click close two of them.

---

### Post by ugm6hr on 2007-05-19
I know this is an old post, but I have managed to develop the same problem in Xubuntu7.04.  I think it's my own fault - I ran nm-applet 3 times (because I thought it wasn't working), and now I can't get rid of the extras.

Anyone found a solution?

I have found that xfce panel setup doesn't include any information on systray4 at all.  So presumably, what is displayed in the "Systray" is under the control of the GNOME Network Manager.

---

### Post by ugm6hr on 2007-05-20
Solved. Just un-install network-manager-gnome and reinstall.  Then run "nm-applet" in Terminal.

---

### Post by PippoPippo on 2007-07-21
Hi,

open the file ~/.cache/.sessions/xfce4-session-????? and remove all entries of nm-applet but one. Renumber the Client? headings appropriately and set Count equal to the last client number + 1. Save. Logout w/out saving the session and you are done.

GIulio

---

