---
title: "Netbook Remix"
date: 2008-11-05
forum: Desktop Environments
---

### Post by Dahaka14 on 2008-11-05
I am trying to install Netbook Remix on 8.10.  I added the sources to my sources.list.  Now, however, I get

peter@peter-laptop:~$ sudo apt-get install go-home-applet human-netbook-theme maximus netbook-launcher window-picker-applet
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  go-home-applet: Depends: libgnome-desktop-2 (>= 1:2.22) but it is not installable
  human-netbook-theme: Depends: gtk2-engines-ubuntulooks but it is not going to be installed
E: Broken packages

After this, I installed gtk2-engines-ubuntulooks, but I still got this message.  Also, I tried to install libgnome-desktop, but it turns out I already have libgnome-desktop-2-7 installed in Synaptic.  What can I do?

---

### Post by mfox on 2008-11-07
This is a longshot, but might you have used the Hardy sources for remix instead of the Intrepid ones?

---

