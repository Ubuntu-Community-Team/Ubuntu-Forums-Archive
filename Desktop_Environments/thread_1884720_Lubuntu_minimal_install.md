---
title: "Lubuntu minimal install"
date: 2011-11-21
forum: Desktop Environments
---

### Post by Joseph L. Casale on 2011-11-21
After using the mini.iso to install I setup the following:

sudo apt-get install openssh-server openssh-client --no-install-recommends
sudo apt-get install python-software-properties
sudo apt-get install lubuntu-core --no-install-recommends

Now it boots to a blank screen, but the other consoles show a login prompt, any idea what is minimally required in addition?

Thanks

---

### Post by hhh on 2011-11-21
-edit- First try not installing anything, just login at the command prompt and then run...```
startx
``` /edit

Usually, after a minimum install, what's needed is xorg for a graphic session and alsa-base (or pulse) for sound, but lubuntu-core should have pulled in xorg (--no-install-recommends did nothing since the dependencies in this case are required)...
[http://packages.ubuntu.com/oneiric/lubuntu-core](http://packages.ubuntu.com/oneiric/lubuntu-core)

I think the next package I'd try would be lubuntu-default-settings...
[http://packages.ubuntu.com/oneiric/lubuntu-default-settings](http://packages.ubuntu.com/oneiric/lubuntu-default-settings)

If that still doesn't work, go ahead and install lubuntu-desktop and take note of what it's installing. It will be heavier than you want, but at least you'll know if your original mini install worked. You can then remove it...```
sudo apt-get purge lubuntu-desktop
```... and start re-installing those packages one by one.

---

### Post by papibe on 2011-11-21
I installed Lubuntu using the minimnal installation method. I follow the steps of this [guide]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall"). That is, the steps for the full install.

For me, the difference is that the key package is called **lubuntu-desktop**.

Just a thought.
Regards.

---

### Post by Joseph L. Casale on 2011-11-21
Thanks for the detailed help, while I was trying to troubleshoot this I did notice a startx bailed so a quick web search for the obvious yielded lack of support for 11.10 in esxi5 :(

Connecting to a remote 4.1 host to attempt my setup...

Thanks!

---

