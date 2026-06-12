---
title: "Gnome Shell Update Gone Bad, Want to go to 3.6 or back to 3.4"
date: 2013-02-06
forum: Desktop Environments
---

### Post by kendoori on 2013-02-06
I was hoping to use the TopIcons Shell Extension with my 12.04/Gnome Shell 3.4 setup, but it seems that 3.6 is required. When I went to upgrade to 3.6, I ended up with 3.5.4 and none of my extensions worked. I was also unable to sucessfully run the extension updater. I tried to go back to 3.4 and purged the PPAs, but in spite of having no references to gnome-team or ricotz in my PPAs, I was unsuccessful. I'm temporarily using Unity while I figure out my next move (e.g. wipe and install 12.10)

I'm now in no mans land. When I try to install Gnome shell from CLI I get the following:

[CODE][
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gnome-shell : Depends: libgcr-3-1 (>= 3.4.0) but 3.2.2-2ubuntu4 is to be installed
               Depends: gir1.2-gcr-3 but it is not installable
E: Unable to correct problems, you have held broken packages.
/CODE]

My preference would be to go to 3.6 (or higher) and update my extensions. 

Any advice is appreciate.

---

