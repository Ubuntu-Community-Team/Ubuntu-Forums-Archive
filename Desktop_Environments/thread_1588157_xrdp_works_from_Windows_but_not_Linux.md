---
title: "xrdp works from Windows but not Linux?"
date: 2010-10-04
forum: Desktop Environments
---

### Post by DaleEMoore on 2010-10-04
Thanks to everyone that's gotten xvnc and xrdp working so I can RDP to an Ubuntu machine then login as the appropriate user. mstsc works fine from WindowsServer2003 to my Ubuntu10.04 server setup with xrdp.

Sadly rdesktop does not work from Ubuntu10.10beta to Ubuntu10.04 that works from WindowsServer2003. Ubuntu10.10beta RDPs fine to lots of windows machines without problem. But not to Ubuntu10.04.

Any suggestions as to the procedure I should use to diagnose what's failing and correct the problem are very much appreciated,
Dale E. Moore

---

### Post by phaedon on 2010-10-04
Do you get any error messages from xrdp?  I would check /var/log/sesman.log /var/log/xrdp-sesman.log

---

### Post by DaleEMoore on 2010-10-05
On the xrdp server there is nothing added to /var/log/sesman.log, and there is no xrdp-sesman.log.

---

### Post by phaedon on 2010-10-05
So when you rdp from 10.10 to 10.04 do you get the dialog box to login?

---

### Post by DaleEMoore on 2010-10-05
No it goes directly to the black box and never does anything else.

---

### Post by phaedon on 2010-10-05
I'm not really to sure.  Things you can try are lowering the colors and resolution of the rdp connection, run rdesktop from the command line to make sure there isn't anything weird in your grdesktop.  Something I would consider as well is installing X11rdp and connection that way.  I've found it to work a little better rather than rdp through vnc.  It takes a bit to get it to compile but seems to run better.  You can download it from [http://server1.xrdp.org/xrdp/x11rdp_xorg71.tar.gz](http://server1.xrdp.org/xrdp/x11rdp_xorg71.tar.gz)

---

### Post by DaleEMoore on 2010-10-06
Your rdesktop suggestion has proven invaluable, thanks! rdestop alone comes up just fine.

Now I can fiddle with grdesktop settings and figure out why mstsc works out of the box but grdesktop fails with default settings.

Thanks for taking the time!
Dale

---

### Post by phaedon on 2010-10-06
No problem glad I could help.

---

