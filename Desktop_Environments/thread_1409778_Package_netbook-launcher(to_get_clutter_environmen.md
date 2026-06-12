---
title: "Package netbook-launcher(to get clutter environment) not working in desktop."
date: 2010-02-18
forum: Desktop Environments
---

### Post by prasanthp on 2010-02-18
As per the link given below, i have installed netbook-launcher on my desktop in order to get clutter environment on desktop. I am using Ubuntu as OS.

(  [http://ubuntu.igameilive.com/2009/03...u-desktop.html]("http://ubuntu.igameilive.com/2009/03/netbook-launcher-in-ubuntu-desktop.html")  )

Package has been installed with some warning as below.

dpkg -i netbook-launcher_2.1.12-0ubuntu3_i386.deb 
(Reading database ... 64824 files and directories currently installed.)
WARNING: node <gettext_domain> not understood below <schema>
WARNING: node <gettext_domain> not understood below <schema>
WARNING: node <gettext_domain> not understood below <schema>
WARNING: node <gettext_domain> not understood below <schema>
WARNING: node <gettext_domain> not understood below <schema>
WARNING: node <gettext_domain> not understood below <schema>
WARNING: node <gettext_domain> not understood below <schema>
WARNING: node <gettext_domain> not understood below <schema>
Unpacking replacement netbook-launcher ...
Setting up netbook-launcher (2.1.12-0ubuntu3) ...
WARNING: node <gettext_domain> not understood below <schema>
WARNING: node <gettext_domain> not understood below <schema>
WARNING: node <gettext_domain> not understood below <schema>
WARNING: node <gettext_domain> not understood below <schema>
WARNING: node <gettext_domain> not understood below <schema>
WARNING: node <gettext_domain> not understood below <schema>
WARNING: node <gettext_domain> not understood below <schema>
WARNING: node <gettext_domain> not understood below <schema>
Processing triggers for man-db ...



Now I am not getting the clutter effect. How to resolve the problem. 
Desktop icons has gone and i am not able to right click now. 

But how to get the effect of desktop icons arrangement.
Can anybody help.

Thanks in advance.

---

### Post by prasanthp on 2010-02-22
I have compiled the package from source and once again installed..
Still i am not getting the clutter effect.
While running the command netbook-launcer, i am getting the output like this 

netbook-launcher
(netbook-launcher:2026): libnetbook-launcher-DEBUG: CONFIG: Low graphics
mode: False
(netbook-launcher:2026): libnetbook-launcher-DEBUG: CONFIG: Font dpi:
96.000000
(netbook-launcher:2026): libnetbook-launcher-DEBUG: CONFIG: Font  changed:
Sans 10

(netbook-launcher:2026): libnetbook-launcher-DEBUG: CONFIG: Connecting  to
ConsoleKit for suspend/resume restarting
(netbook-launcher:2026): liblauncher-DEBUG: launcher-menu.c:361
(netbook-launcher:2026): liblauncher-DEBUG: Workarea: (0, 25) (0, 0)
Segmentation fault

Can anybody help me in this issue.

---

