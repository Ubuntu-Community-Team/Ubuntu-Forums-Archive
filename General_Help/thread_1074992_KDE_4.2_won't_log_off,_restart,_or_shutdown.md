---
title: "KDE 4.2 won't log off, restart, or shutdown"
date: 2009-02-19
forum: General Help
---

### Post by AeroNautica0909 on 2009-02-19
Here's the problem I'm having:

I'm using Ubuntu Intrepid Ibex with GNOME 2.24 and KDE 4.2 installed simultaneously. I was trying to get Compiz to run since I know how to configure that and I like the effects it provide even though KDE 4.2 comes with its own effects. Something went wrong to the point that KDE 4.2 wouldn't log off, shutdown, or restart, even when I went to submit the command.

So I completely uninstalled KDE 4.2 and removed the old settings. I went to reinstall KDE 4.2 and the same problem persists. Any suggestions on what I can do so I can actually have a fully functional KDE 4.2 as I had before?

I've been having a hard time for quite awhile trying to get Compiz to work with KDE- with 3.5.10 and now with 4.2. Any suggestions on this would be greatly appreciated too. Thanks!

---

### Post by AeroNautica0909 on 2009-03-30
I figured it out. I was running Cairo Dock and it was set to automatically load. I originally set it to do so using GNOME's Session applet in the Control Center. Somehow using that applet to automatically load Cairo Dock kept KDE 4.2 from ending it session.

I removed Cairo Dock from the applet and KDE 4.2 can log off, shut down, etc. Cairo Dock automatically loads in KDE 4.2 but now not in GNOME. I created another thread for that problem.

---

