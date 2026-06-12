---
title: "Loading nvidia-settings before GNOME login screen"
date: 2005-06-16
forum: Desktop Environments
---

### Post by MonkeyWrench32 on 2005-06-16
Is there a way I can run the command "nvidia-settings -l" before the Ubuntu GNOME login screen appears?  Right now I have it started up in the sessions with my main account, but I'd like it to be global.

---

### Post by tristan on 2005-06-16
And, is there any way to start coolbits nvidia overclocking automatically with 7664 dirver? I'm lazy and get sick of having to fire up nvidia settings, and going through the overclocking rigmarole every time I want to plat Doom3...

---

### Post by MonkeyWrench32 on 2005-06-16
Bump.

---

### Post by hondje on 2005-06-16
Go to System -> Preferences -> Sessions -> Startup Programs tab, and add /usr/bin/nvidia-settings --load-config-only

---

### Post by MonkeyWrench32 on 2005-06-16
[QUOTE=hondje]Go to System -> Preferences -> Sessions -> Startup Programs tab, and add /usr/bin/nvidia-settings --load-config-only[/QUOTE]
 I have that already like that.  I just want to know if I can run that somehow before the login screen appears so it will work for any account.

---

### Post by hondje on 2005-06-17
Just put the options in your xorg.conf file, then, and when X fires up it'll load them with it.  The syntax for the options is available in nvidia's readme.

---

### Post by BobBlum on 2006-11-14
> **hondje said:**
> Just put the options in your xorg.conf file, then, and when X fires up it'll load them with it.  The syntax for the options is available in nvidia's readme.

Regarding /usr/bin/nvidia-settings --load-config-only

Where in xorg.conf do I place this syntax?

Thanks,

  Bob

---

