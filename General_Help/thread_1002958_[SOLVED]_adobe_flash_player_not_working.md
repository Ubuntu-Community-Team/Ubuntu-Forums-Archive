---
title: "[SOLVED] adobe flash player not working"
date: 2008-12-05
forum: General Help
---

### Post by dmzr on 2008-12-05
Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. Get the latest Flash player. This is the message I am getting. I did a wubi install and am having this problem with flash player?
When I click on link for flash I am asked to select a version from this list
.tar.gz for linux
.rpm
 YUM for linux
.deb for ubunta 8.04
When I look in system/about ubunta   I find this, Ubuntu 8.10 - the Intrepid Ibex - released in October 2008.I am sure that my gateway profile 5 is a 32 bit machine but how do I learn if I have a 32 or 64 bit copy of intrepid ibex installed? or does it matter? thanks for any and all help given, lm
				
ps I do have java enabled

---

### Post by spcwingo on 2008-12-05
Download the tar.gz version and extract it.  Then open a terminal and cd to the extracted directory.  Then type sudo ./flashplayer-installer.  It'll tell you to close all open browsers.  Then ask where the installation directory is.  It's either /usr/lib/firefox-3.0.4 (or whatever version you're running), /usr/lib/firefox, or /usr/lib/mozilla.  Try them in that order.  Let me know how it turns out for you.

---

### Post by barisurum on 2008-12-05
An easier way would be:

Open synaptic, find the package flashplugin-nonfree and install it. It will install all the needed dependencies. Then flash should work.

---

### Post by dmzr on 2008-12-05
I opened synaptic, found the package flashplugin-nonfree and installed it. It worked   flash just works.It did all the work downloading tar.gz and extracting it .. easy is cool thanks for the help. happy holidays...lm
__________________

---

