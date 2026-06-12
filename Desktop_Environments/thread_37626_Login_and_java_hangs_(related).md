---
title: "Login and java hangs (related?)"
date: 2005-05-27
forum: Desktop Environments
---

### Post by shooz on 2005-05-27
Hey all -

I'm running an up to date Hoary 5.04 on a Thinkpad t40p, and suddenly I am having two strange and possibly related problems.  Ocassionally when I first boot up and log in, the desktop startup process hangs and I never see the splash screen that shows the startup progress.  I can hit ctrl alt delete and try to log in again, but it hangs every time.  If I reboot and try it again, it usually works.

I am also having a possibly related issue with java.  Sometimes when I launch a java application (like jEdit or Azureus), it hangs.  jEdit will show its spash screen and its progress bar will increase by one notch, but then it will stop.  Azureus never shows any UI at all.  But then I reboot and things run with no problem!

Anyone have any ideas?  This is the first problem I've had with Ubuntu since switching from debian unstable.

thanks!
shooz

---

### Post by shooz on 2005-05-27
Ok, I hate to answer my own thread, but one problem I did not describe with java (starting up an internal JVM in Eclipse was hanging as well) was solved by doing a ifup lo.  I think the reason why the lo device wasn't up was that I've been using ctrl-c to abort the "Configuring Netoworks..." startup step when I boot because it takes a long time to time out when it does not find a wireless network.

This may be the cause of my other problems -- I will post if it turns out this way.

cheers,
shooz

---

