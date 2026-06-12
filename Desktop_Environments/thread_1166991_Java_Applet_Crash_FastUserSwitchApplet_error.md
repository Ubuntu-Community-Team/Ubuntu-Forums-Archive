---
title: "Java Applet Crash: FastUserSwitchApplet error"
date: 2009-05-22
forum: Desktop Environments
---

### Post by paradoxic on 2009-05-22
Often when I load Java applets in Firefox my firefox will just shutdown. Sometimes simple applets work, but most crash. In one case a Java applet completely crashes my system and the computer screen goes black for a second and then comes back to the login screen (GNOME seems to have crashed). Then when I log back in I got this message:
The panel encountered a problem while loading "OAFIID:GNOME_FastUserSwitchApplet".

Thanks in advance.

---

### Post by cyprys on 2009-11-02
It's a common problem after upgrade to Karmic. I don't know why there's no fix yet - didn't find any on launchpad at least. Try ```
sudo apt-get install --reinstall gnome-applets gnome-applets-data
``` and also make sure your panel is at last 25px height (**RMB on the panel -> Properties -> Size**). There's no guarantee but it might help.

---

### Post by ionFreeman on 2009-11-06
Thanks, cyprys. My panel was set to 24 pixels high, so now I have great hope for the future. I let GNOME delete the applet, though, and I don't see it on RMB -> Add To Panel. How do I get the applet back?

---

### Post by cyprys on 2009-11-13
```
sudo apt-get install indicator-applet libempathy30 indicator-session indicator-applet-session
```

In my case: I deleted Empathy and since indicator-applet-session (which is the package containing new fast-user-switch-applet) depends on libempathy30 it couldn't run.

BTW, some off-topic: Really smooth, Canonical! I need Empathy's libs installed in order to get basic system functionalities available (such as logging out or shutting down my gear for example). And I don't even use Empathy since it lacks many compared to pidgin - why the change anyway?

edited:
Please, mark this thread as SOLVED if you've resolved your problem.

---

