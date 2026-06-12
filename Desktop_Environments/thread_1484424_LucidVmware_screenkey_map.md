---
title: "Lucid/Vmware screen/key map"
date: 2010-05-15
forum: Desktop Environments
---

### Post by gerryg001 on 2010-05-15
Latest Lucid with vmware server 2. Been using vmware okay with Hardy for a long time. Testing now on a laptop to see if the combination will work. Upgrade of laptop from Karmic seemed fine. Lucid host okay, only vmware Karmic guest has problem.

Found the vmware/firefox plugin issue, and regressing to ff 3.5.8 allows launching a Karmic guest I copied from another machine.

However, moving cursor (touchpad) towards right side of guest window loses the cursor and changes to a hand/finger. Some keyboard keys (e.g. arrows) don't map properly. Appears like X11 settings are wrong.

/1508704#1508704"]http://communities.vmware.com/message/1508704#1508704[/URL]

Above mentioned keyboard login (only) problems, but login's fine. They suggested > dpkg-reconfigure console-setup, but nothing there matches my lenovo G350 and I'd rather not experiment as the screen's also weird.

---

