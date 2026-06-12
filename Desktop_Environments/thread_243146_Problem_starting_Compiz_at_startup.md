---
title: "Problem starting Compiz at startup"
date: 2006-08-24
forum: Desktop Environments
---

### Post by RadixLecti on 2006-08-24
I've tried to find anything concerning my problem, but haven't found anything.

I've followed the guide in the wiki ([https://help.ubuntu.com/community/CompositeManager/InstallingCompiz](https://help.ubuntu.com/community/CompositeManager/InstallingCompiz)) to a tee, after having set up xgl as a session.

It works, as long as I leave the terminal on. If I shut that down, I get borderless windows. I've gotten around that by starting cgwd and compiz with the "Run an application" widget, but when I reboot, I get borderless windows by default. No wobbly tooltips or menus, either (except on some logins, for some reason).

My hunch is that my "sessions" is borked. I've tried to install compiz numerous times, and reinstalling Ubuntu... without touching my /home partition.

If I start System -> Preferences -> Sessions and look under Startup Programs, theres a post that says "compiz --replace gconf", that I can't remove. I can edit it, but not remove it. I have configured gconf-editor to start Compiz with all plugins in the correct (I think) order, as per the wiki. I have doublechecked.

cgwd is among the startup programs in Sessions too.

Is there an order I should try to get cgwd and compiz to start up nice at login? Is there a way for me to remove the configuration of Sessions, and if so, where do I find it?

Or have I done something totally wrong?

---

### Post by Dinerty on 2006-08-24
I just insalled xgl/compiz myself tonight using this guide I also had a problem with the borders disapearing, but they returned once I did

```
cgwd &
```

sorry i cant be more help

---

### Post by RadixLecti on 2006-08-27
*bump*

Can anyone help me? Can't seem to get Compiz going at all now. No error messages, just windowless borders.

---

