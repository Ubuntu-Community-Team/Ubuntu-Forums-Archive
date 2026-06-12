---
title: "gnome-terminal require password at start"
date: 2010-07-09
forum: Desktop Environments
---

### Post by tenhi on 2010-07-09
Hi there!
I'm usingg Ubuntu 10.04.

Yesterday i've got faced with an issue that was very strange for me.

When i start gnome-terminal  (from terminal or gui) at the first i see invite to enter sudo pass: Terminal window is opening and i see the string: 

[I][sudo] password for tenhi: 
[/I]
So could someone be so kind to explain why it appears? Yesterday i changed .bashrc file and some settings in User and Groups management.

Google does not have any idea about this issue...

Regards.;)

---

### Post by tenhi on 2010-07-09
yo) it's me again. I thinked of why it asks me. I have added a command for blocking touchpad 

sudo modprobe -r psmouse

in .bashrc file.

So i think when you start a terminal in reads .bashrc and see sudo and baang :)

Any suggestions where I have to put this command to run in correctly?

---

### Post by mcduck on 2010-07-09
You are correct, if you add a command that uses sudo into your bashrc then it will try to execute it when you open a terminal (that's pretty much the idea of bashrc ;))..

If you want to disable the psmouse module then just blacklist it by adding it to /etc/modrobe.d/blacklist.conf. This will stop the system from loading that module in the first place, so you don't need to remove it after the system is already running like you are now trying to do.

---

### Post by tenhi on 2010-07-09
Good.That's it. Thanks a lot!

---

### Post by jodorami on 2012-03-28
> **tenhi said:**
> Good.That's it. Thanks a lot!

Seems like I've run into the same problem. But unlike you, I don't quite understand the hints given in this thread. Could someone please spell them out for me? 

Thanks!

---

