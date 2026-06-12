---
title: "Some applications won't launch on Ubuntu"
date: 2015-10-19
forum: Desktop Environments
---

### Post by Bibrak on 2015-10-19
My Document viewer is not able to launch. When I open it using commandline it gives me the following error:

```
evince
evince: error while loading shared libraries: libffi.so.6: failed to map segment from shared object: Permission denied
```

when I sudo it gives me the following error:

```

sudo evince ass3.pdf 
No protocol specified

** (evince:13785): WARNING **: Could not open X display
No protocol specified
error: XDG_RUNTIME_DIR not set in the environment.
Cannot parse arguments: Cannot open display: 


```

How to make it open normally, by normally I mean when I click on a pdf with my mouse?

---

### Post by TheFu on 2015-10-19
Do NOT use sudo to run GUI applications.
Do NOT use sudo to run GUI applications.
Hopefully that didn't screw up the config files. Go and check those first.
~/.config/evince and below there.

Next - lets try removing evince then reinstalling it.
```
sudo apt-get remove evince evince-common
sudo apt-get install evince
```
These are the easy things. If that doesn't work, we'll have to look at what else has been installed which is causing the conflict.  That is a much harder issue, unfortunately.

BTW, you can use *sudo -H application* - to run apps, but once you have a good grasp of file and directory permissions, it shouldn't be needed ... like ... ever.

Lastly, which DE are you running? Clicking on a file is filer/DE specific, methinks.

---

### Post by Bibrak on 2015-10-23
I tried removing and again installing evince but no luck. 

I checked the config files and there are two of them 

ls ~/.config/evince/
accels  print-settings

---

### Post by marcus_s on 2015-10-24
It appears as if SELinux is the cause of the issue. I found this interesting comment in Google Groups, where someone had issues with his Apache server:

> I had the same prob. Turns out SELinux is on & causing the issue. Either configure SELinux to enable loading passenger module or disable SELinux.

Source: [https://groups.google.com/forum/#!msg/phusion-passenger/_pAIvpeWVfU/euHMj002iS8J](https://groups.google.com/forum/#!msg/phusion-passenger/_pAIvpeWVfU/euHMj002iS8J)

Maybe that helps

---

### Post by TheFu on 2015-10-24
Er ... except that Ubuntu doesn't install selinux by default. 
Ubuntu uses apparmor.

---

