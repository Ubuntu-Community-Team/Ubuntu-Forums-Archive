---
title: "Steam for Linux doesn't run."
date: 2013-08-27
forum: Gaming &amp; Leisure
---

### Post by schhhhhhhhcss on 2013-08-27
I recently installed Steam for Linux**[™]("http://en.wikipedia.org/wiki/Trademark_symbol")  **and it doesn't run! 

When I try to run it through the Terminal this tends to appear:

[B]Running Steam on ubuntu 12.04 64-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(1374875626_client)
Installing breakpad exception handler for appid(steam)/version(1374875626_client)
Installing breakpad exception handler for appid(steam)/version(1374875626_client)
unlinked 0 orphaned pipes
Installing breakpad exception handler for appid(steam)/version(1374875626_client)
Steam: An X Error occurred
X Error of failed request:  BadRequest (invalid request code or no such operation)
Major opcode of failed request:  153 (GLX)
Minor opcode of failed request:  19 (X_GLXQueryServerString)
Serial number of failed request:  34
xerror_handler: X failed, continuing
Steam: An X Error occurred
X Error of failed request:  BadRequest (invalid request code or no such operation)
Major opcode of failed request:  153 (GLX)
Minor opcode of failed request:  19 (X_GLXQueryServerString)
Serial number of failed request:  62
xerror_handler: X failed, continuing
Steam: An X Error occurred
X Error of failed request:  BadRequest (invalid request code or no such operation)
Major opcode of failed request:  153 (GLX)
Minor opcode of failed request:  14 (X_GLXGetVisualConfigs)
Serial number of failed request:  90
xerror_handler: X failed, continuing
glXChooseVisual failedadrian@adrian-Inspiron-530s:[/B]

---

### Post by kschlichther on 2013-08-27
If you installed through software centre, you should probably make sure the other parts of your OS are up to date. Open terminal do sudo apt-get update and run the software updater program afterwards to make sure your kernel is an up-to-date version. Otherwise just upgrade to Ubuntu 13.04.

---

### Post by DarkAmbient on 2013-08-27
Also make sure you got proper drivers installed for you GPU.

---

### Post by oldrocker99 on 2013-08-27
> **DarkAmbient said:**
> Also make sure you got proper drivers installed for you GPU.

And here's how:

sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update && sudo apt-get upgrade

And good luck!

---

### Post by houstonbofh on 2013-08-30
I am running it fine on 12.04, and it was working fine with the standard nvidia drivers. (But I wen to the "experimental to kill the nag screen)

So, to the OP...  You look like you are having a GLX issue.  What video card do you have, and what drivers are you running?  Have you tried Gnome Classic 2d mode?

---

### Post by bibek2 on 2013-09-03
looks like an OpenGL issue. try glxinfo |grep "OpenGL version" and see if your current driver supports it.

---

