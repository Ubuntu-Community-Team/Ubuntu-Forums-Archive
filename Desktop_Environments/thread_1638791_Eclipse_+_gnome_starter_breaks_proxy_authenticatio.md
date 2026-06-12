---
title: "Eclipse + gnome starter breaks proxy authentication"
date: 2010-12-06
forum: Desktop Environments
---

### Post by ubart on 2010-12-06
I have Eclipse 3.6 (Helios) installed from a zip file (not from the repositories).
Since I'm behind a proxy I followed the instructions from the readme/readme_eclipse.html file, and added the enableGnome option to the eclipse.ini file.

> Enabling GNOME proxy support

GNOME applications can make use of proxy settings defined in this environment. If set, Eclipse will use it prior to proxy settings declared using env variables. This feature is disabled by default, to enable it launch Eclipse with "-Dorg.eclipse.core.net.enableGnome" switch. That is,

eclipse -Dorg.eclipse.core.net.enableGnome

Everything works fine as long as I start Eclipse from the terminal. If I create a Starter on the desktop or in a panel Eclipse can not authenticate against the proxy. I have tried setting the starter option to open the application in a terminal but that doesn't help. Adding the switch to the starter command (instead of the ini file) does not help either.
Error example:
> HTTP Proxy Authentication Required: [https://dl-ssl.google.com/android/eclipse/site.xml](https://dl-ssl.google.com/android/eclipse/site.xml)
HTTP Proxy Authentication Required: [https://dl-ssl.google.com/android/eclipse/site.xml](https://dl-ssl.google.com/android/eclipse/site.xml)
Proxy Authentication Required
Checking for Upgrades or installing new software is not possible.

Am I missing something here or is it a bug? Is it a Gnome problem or is it Eclipse?

---

