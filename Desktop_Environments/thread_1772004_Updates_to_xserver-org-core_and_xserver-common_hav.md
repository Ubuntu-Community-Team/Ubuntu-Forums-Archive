---
title: "Updates to xserver-org-core and xserver-common have crashed Gnome3"
date: 2011-05-31
forum: Desktop Environments
---

### Post by maverick280857 on 2011-05-31
Hi

I am running Ubuntu Natty Narwhal 11.04 and Gnome3 on my Dell XPS 15 laptop (NVIDIA GT435M). A few hours ago, the following packages got updated 

xserver-org-core (1.10.1-1ubuntu1, 1.10.1-ubuntu1.1)
xserver-common   (1.10.1-1ubuntu1, 1.10.1-ubuntu1.1)

Now, I am not able to log into Gnome3. The first time, I got an error message saying Gnome3 failed to load and will switch to fallback mode, because my system hardware is not capable of running Gnome3. 

On subsequent logins, this message did not show either.

I am also unable to access OpenGL/GLX settings in nvidia-settings.

Any ideas on how to fix this?

---

### Post by maverick280857 on 2011-05-31
Found a fix

```

sudo mv /usr/lib/xorg/modules/extensions/libglx.so /usr/lib/xorg/modules/extensions/libglx.so.orig
sudo ln -s /usr/lib/xorg/modules/extensions/libglx.so.270.41.06 /usr/lib/xorg/modules/extensions/libglx.so

```

The version number '270.41.06' may be different for different people.

---

