---
title: "screenlets autostart issues"
date: 2009-04-08
forum: Desktop Environments
---

### Post by lovinglinux on 2009-04-08
I'm experiencing problems with screenlets when they are configure to autostart on login. Sometimes they all load in the wrong workspace, sometimes a few load in one workspace and others on another.

I don't know if this is a problem with screenlets or if compiz is changing the workspace order. Anyway, is pretty annoying.

Any ideas?

---

### Post by Nathanael Culver on 2009-04-08
> **lovinglinux said:**
> I'm experiencing problems with screenlets when they are configure to autostart on login. Sometimes they all load in the wrong workspace, sometimes a few load in one workspace and others on another.

Your error sounds like this reported bug:

[https://bugs.launchpad.net/screenlets/+bug/345359](https://bugs.launchpad.net/screenlets/+bug/345359)

The whole thing's pretty flaky. I've spent hours playing with it, but still every time I log in or click Restart All in the screenlets UI I get multiple instances of several screenlets. Some screenlets I can't disable Start/Stop -- the setting just reasserts itself when I try. Others insist on being sticky or widgets or always on top no matter how often I uncheck those settings.

I can't offer you any help, just a Me Too. But it looks like it may be fixed in CVS, just have to wait for the next update.

---

### Post by lovinglinux on 2009-04-08
Thanks. At least now I know it's a known bug.

---

