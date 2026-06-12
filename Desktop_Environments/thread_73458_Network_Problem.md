---
title: "Network Problem"
date: 2005-10-09
forum: Desktop Environments
---

### Post by sathan on 2005-10-09
Hi all.

I've got a problem with my kubuntu, I installed three days ago and everything worked fine, I switched off yesterday and this morning I start the system but the network doesn't work, I have tried to start the network service but it fails all the time.

The first time I configured my net was through the preferences in konqueror but now when I open it, it says that the interface is disabled and doesn't allow me to enable it back again...


I need your help desperately

---

### Post by mlomker on 2005-10-09
> The first time I configured my net was through the preferences in konqueror but now when I open it, it says that the interface is disabled and doesn't allow me to enable it back again.

Are you going into Control Center under Internet & Network, Network Settings?

---

### Post by Takis on 2005-10-09
You can't change your network settings with your normal id. You'll need to hit 'Administrator Mode' (should be in the bottom left) and enter your password. However, Control Centre's buggy at the moment so what you may like to do instead is (from a terminal, for example Konsole) run ```
sudo kcontrol
```
This will let you edit your network settings.

---

### Post by mlomker on 2005-10-09
> sudo kcontrol

So it wasn't just me!  I always had to go into it by putting **kdesu kcontrol** onto the run command line in Hoary.  I just installed Breezy today and it appears to be fixed now.

---

