---
title: "Startup and Shutdown questions"
date: 2006-08-11
forum: Desktop Environments
---

### Post by utherwayn on 2006-08-11
What is the recommended way to manage startup and shutdown process's in Kubuntu?

I want to be able to add and remove them and the KDE Bootup manager doesnt seem to let me do that.

For example, right now KNetworkManager isn't loading on startup for some reason and i have to 'sudo dhclient' everytime I start up my laptop.  It's mildly annoying.  I would prefer to do the work through some sort of script if one is necessary, im sure theres some shell command out there that I just don't know about, thats why I'm asking here.

---

### Post by Neobuntu on 2006-08-11
Unless your having two driver/modules fighting for your ethernet device (and maybe that's causing intermitant outages or hangs), you should be able to check the box where it starts up on boot.

System Setting > Network Settings and click "Administrator mode"

Enter password and...

Click the device you want before "configure" and note the...
"Activate When Computer Starts" check box.

Hope that's what you need. ;)

---

