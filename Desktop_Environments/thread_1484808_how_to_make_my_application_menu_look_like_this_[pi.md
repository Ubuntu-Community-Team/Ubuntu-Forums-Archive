---
title: "how to make my application menu look like this [pic included]"
date: 2010-05-16
forum: Desktop Environments
---

### Post by Elie-M on 2010-05-16
I want to make the drop down and tab menu look like this pic

[IMG]http://www.linux.com/images/file/Ubuntu_Netbook_Remix.png[/IMG]


any help? thx

---

### Post by qwerty2009 on 2010-05-16
[click here to install launcher]("apt:netbook-launcher?section=universe?section=multiverse")

[click here to install go-home applet]("apt:go-home-applet?section=universe?section=multiverse")

restart then delete your menu-bar from panel
ad go-home-applet to panel done:D

---

### Post by Elie-M on 2010-05-16
thanks man but I'm facing problems running it ... it doesnt run..

With netbook-launcher:

** (process:3081): DEBUG: OpenGL renderer string: Mesa DRI Mobile Intel? GM45 Express Chipset GEM 20100330 DEVELOPMENT x86/MMX/SSE2

(netbook-launcher:3081): libnetbook-launcher-DEBUG: CONFIG: Low graphics mode: True
(netbook-launcher:3081): libnetbook-launcher-DEBUG: CONFIG: Font dpi: 96.000000
(netbook-launcher:3081): libnetbook-launcher-DEBUG: CONFIG: Font changed: Sans 10

(netbook-launcher:3081): libnetbook-launcher-DEBUG: CONFIG: Connecting to ConsoleKit for suspend/resume restarting
(netbook-launcher:3081): liblauncher-DEBUG: launcher-menu.c:361
ORPHAN: Ubuntu Software Center
(netbook-launcher:3081): liblauncher-DEBUG: Workarea: (0, 24) (0, 23)
** (netbook-launcher:3081): DEBUG: Not loading modules: Error opening directory '/usr/lib/netbook-launcher/plugins': No such file or directory


With Sudo Netbook-Launcher:

** (process:3599): DEBUG: OpenGL renderer string: Mesa DRI Mobile Intel? GM45 Express Chipset GEM 20100330 DEVELOPMENT x86/MMX/SSE2

** (netbook-launcher:3599): DEBUG: Created local applications directory at /root/.local/share/applications
** (netbook-launcher:3599): DEBUG: Created local applications directory at /root/.config/netbook-launcher/cache
** (netbook-launcher:3599): DEBUG: Created local icons directory at /root/.config/netbook-launcher/icons
(netbook-launcher:3599): libnetbook-launcher-DEBUG: CONFIG: Low graphics mode: False
(netbook-launcher:3599): libnetbook-launcher-DEBUG: CONFIG: Font dpi: 96.000000
(netbook-launcher:3599): libnetbook-launcher-DEBUG: CONFIG: Font changed: Sans 10

(netbook-launcher:3599): libnetbook-launcher-DEBUG: CONFIG: Connecting to ConsoleKit for suspend/resume restarting
(netbook-launcher:3599): liblauncher-DEBUG: launcher-menu.c:361
ORPHAN: Ubuntu Software Center
(netbook-launcher:3599): liblauncher-DEBUG: Workarea: (0, 24) (0, 23)
** (netbook-launcher:3599): DEBUG: Not loading modules: Error opening directory '/usr/lib/netbook-launcher/plugins': No such file or directory

---

### Post by KlavKalashj on 2010-05-16
> **Elie-M said:**
> thanks man but I'm facing problems running it ... it doesnt run..

With netbook-launcher:

** (process:3081): DEBUG: OpenGL renderer string: Mesa DRI Mobile Intel? GM45 Express Chipset GEM 20100330 DEVELOPMENT x86/MMX/SSE2

(netbook-launcher:3081): libnetbook-launcher-DEBUG: CONFIG: Low graphics mode: True
(netbook-launcher:3081): libnetbook-launcher-DEBUG: CONFIG: Font dpi: 96.000000
(netbook-launcher:3081): libnetbook-launcher-DEBUG: CONFIG: Font changed: Sans 10

(netbook-launcher:3081): libnetbook-launcher-DEBUG: CONFIG: Connecting to ConsoleKit for suspend/resume restarting
(netbook-launcher:3081): liblauncher-DEBUG: launcher-menu.c:361
ORPHAN: Ubuntu Software Center
(netbook-launcher:3081): liblauncher-DEBUG: Workarea: (0, 24) (0, 23)
** (netbook-launcher:3081): DEBUG: Not loading modules: Error opening directory '/usr/lib/netbook-launcher/plugins': No such file or directory


With Sudo Netbook-Launcher:

** (process:3599): DEBUG: OpenGL renderer string: Mesa DRI Mobile Intel? GM45 Express Chipset GEM 20100330 DEVELOPMENT x86/MMX/SSE2

** (netbook-launcher:3599): DEBUG: Created local applications directory at /root/.local/share/applications
** (netbook-launcher:3599): DEBUG: Created local applications directory at /root/.config/netbook-launcher/cache
** (netbook-launcher:3599): DEBUG: Created local icons directory at /root/.config/netbook-launcher/icons
(netbook-launcher:3599): libnetbook-launcher-DEBUG: CONFIG: Low graphics mode: False
(netbook-launcher:3599): libnetbook-launcher-DEBUG: CONFIG: Font dpi: 96.000000
(netbook-launcher:3599): libnetbook-launcher-DEBUG: CONFIG: Font changed: Sans 10

(netbook-launcher:3599): libnetbook-launcher-DEBUG: CONFIG: Connecting to ConsoleKit for suspend/resume restarting
(netbook-launcher:3599): liblauncher-DEBUG: launcher-menu.c:361
ORPHAN: Ubuntu Software Center
(netbook-launcher:3599): liblauncher-DEBUG: Workarea: (0, 24) (0, 23)
** (netbook-launcher:3599): DEBUG: Not loading modules: Error opening directory '/usr/lib/netbook-launcher/plugins': No such file or directory

Just install ubuntu-netbook, log out, change session to the netbook remix/UNE, log in. Tada!

---

### Post by Elie-M on 2010-05-16
all the love for u man, thanks!

---

