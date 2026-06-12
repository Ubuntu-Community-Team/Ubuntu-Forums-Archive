---
title: "totem-gstreamer-firefox-plugin won't install."
date: 2006-08-22
forum: Desktop Environments
---

### Post by neko18 on 2006-08-22
Anyone know what's going on here? It's a new install of Ubuntu 6.06.1. All I've done is set up my WIFI and install some stuff with EasyUbuntu. Please ask if more info is needed.

```
rick@rick-laptop:~$ sudo apt-get install totem-gstreamer-firefox-plugin
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  totem-gstreamer-firefox-plugin: Depends: totem-gstreamer (= 1.4.1-0ubuntu4) but 1.4.3-0ubuntu1 is to be installed
E: Broken packages
rick@rick-laptop:~$
```

As a side note, I've already tried [FONT="Courier New"]sudo apt-get update[/FONT] and [FONT="Courier New"]sudo apt-get upgrade[/FONT].

Edit: I just noticed this in Synaptic and find it kind of odd:
[IMG]http://img208.imageshack.us/img208/1683/totemqd8.png[/IMG]

---

### Post by neko18 on 2006-08-22
Well, I sort of fixed the problem. I just installed totem-xine-firefox-plugin (which adds totem-xine and removes totem-gstreamer).

---

