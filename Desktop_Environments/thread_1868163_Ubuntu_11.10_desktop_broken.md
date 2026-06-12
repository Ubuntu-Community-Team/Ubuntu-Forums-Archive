---
title: "Ubuntu 11.10 desktop broken"
date: 2011-10-23
forum: Desktop Environments
---

### Post by nicholas.reese on 2011-10-23
Hi all,

I carried out an upgrade to Ubuntu 11.10 about two weeks ago. Everything went fine, no problems. The Unity? desktop installed as default - a little bit of getting used to, but I don't mind it now. About a week ago, the desktop broke - I no longer get the side menu popping out, and the menu bar at the top of the screen is stuck on (I think) the file manager menu items. All applications etc. work fine when started (via command line).

I do not want to blow this machine away and start again as I have a lot of development tools set up and configured on it.

I have tried reinstalling (using apt-get) most of the desktop components that I could find reference to, but no luck.

Could someone tell me please how to do a complete re-install of the desktop? Google as I may, I cannot find a working answer.

TIA.

---

### Post by proxygeek on 2011-11-05
I faced the exact same issue today. Have Ubuntu 11.10 installed for last few weeks and it was running fine.

Installed the compizconfig-settings-manager today through the ubuntu software centre, rebooted, and the next thing i know - No Side menu panel popping out, super key not working, no top-menu bar and obviously no indicator applets (not even the log-out button).

Fired up this browser session from terminal.

Any help ppl?

---

### Post by proxygeek on 2011-11-05
> **proxygeek said:**
> I faced the exact same issue today. Have Ubuntu 11.10 installed for last few weeks and it was running fine.

Installed the compizconfig-settings-manager today through the ubuntu software centre, rebooted, and the next thing i know - No Side menu panel popping out, super key not working, no top-menu bar and obviously no indicator applets (not even the log-out button).

Fired up this browser session from terminal.

Any help ppl?


Was able to fix it following this post:
[http://askubuntu.com/questions/63921/unity-3d-doesnt-work-anymore-just-shows-a-menu-on-the-top/63937#63937]("http://askubuntu.com/questions/63921/unity-3d-doesnt-work-anymore-just-shows-a-menu-on-the-top/63937#63937")

Basically, as my Unity 2D was still intact, 

1) at login screen, select unity2d and login

2) install ccsm (compiz config settings manager) sudo apt-get install compizconfig-settings-manager compiz-fusion-plugins-extra

3) start ccsm, select category 'desktop'

enable 'Ubuntu Unity Plugin', if asked to resolve conflicts, select the MIDDLE button for all conflicts.

press: 'Close'

4) restart, select unity (3D) and login

---

### Post by totfit on 2011-11-05
A way I have found to get back to default if I mess up is to show hidden files in my home directory, delete everything in the .compiz folder and everything in the compiz folder withing .config. I merely opened the compiz settings manager and it hosed my desktop. Deleting these brought everything back.

---

### Post by oldrocker99 on 2011-11-05
Seriously, give KDE a try. It's closer to GNOME 2.x than what's being foisted on users these days.

---

