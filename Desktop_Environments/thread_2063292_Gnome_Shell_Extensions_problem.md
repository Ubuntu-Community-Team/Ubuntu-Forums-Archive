---
title: "Gnome Shell Extensions problem"
date: 2012-09-26
forum: Desktop Environments
---

### Post by apple_head on 2012-09-26
Hi All

I am following this tutorial on installing a different gnome theme:
 [http://maketecheasier.com/install-custom-gnome-shell-themes/2011/09/27](http://maketecheasier.com/install-custom-gnome-shell-themes/2011/09/27)

And I have followed it step by step, but when I try to install the gnome-shell-extensions I get this:

```
dan@dan-desktop:~$ sudo apt-get install gnome-shell-extensions
[sudo] password for dan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 gnome-shell-extensions : Depends: gnome-shell (>= 3.5) but 3.4.1-0ubuntu2 is to be installed
E: Unable to correct problems, you have held broken packages.
dan@dan-desktop:~$ 

```

I am using Ubuntu 12.04 Stable release with Gnome 3.

---

### Post by apple_head on 2012-09-27
anyone???

---

### Post by Sonsum on 2012-09-27
It looks like your gnome shell extensions package is looking for Gnome 3.5, a development version of Gnome.

12.04.1 only has Gnome 3.4.2, so this package won't install.

Have you tried visiting [https://extensions.gnome.org/]("https://extensions.gnome.org/") and installing the extensions from there? It's currently the easiest way.

---

