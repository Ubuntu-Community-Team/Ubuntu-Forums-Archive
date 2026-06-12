---
title: "Disable desktop effects permanently"
date: 2011-03-09
forum: Desktop Environments
---

### Post by mikerobinson on 2011-03-09
In the desktop effects configuration screen, "Enable desktop effects" is checked, however the checkbox is grayed out and I can't uncheck it. All I can do is "Suspend desktop effects", but they get reenabled after every login. How do I disable them permanently?

---

### Post by ankspo71 on 2011-03-09
Hi,
Try editing the kwinrc file located in the hidden .kde directory at /home/yourname/.kde/share/config/kwinrc. 

In the [Compositing] section, Look for the line that says:
Enabled=true

Then change it to:
Enabled=false

Then save the file and then try restarting Kubuntu to see if it will keep the desktop effects disabled.

[http://forum.kde.org/viewtopic.php?f=17&t=6712](http://forum.kde.org/viewtopic.php?f=17&t=6712)

Hope this helps

---

### Post by mikerobinson on 2011-03-09
> **ankspo71 said:**
> Hi,
Try editing the kwinrc file located in the hidden .kde directory at /home/yourname/.kde/share/config/kwinrc. 

In the [Compositing] section, Look for the line that says:
Enabled=true

Then change it to:
Enabled=false

Then save the file and then try restarting Kubuntu to see if it will keep the desktop effects disabled.

[http://forum.kde.org/viewtopic.php?f=17&t=6712](http://forum.kde.org/viewtopic.php?f=17&t=6712)

Hope this helps

It did help. Thanks!

---

