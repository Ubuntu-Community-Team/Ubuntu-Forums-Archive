---
title: "Corruption caused by Wine installation?"
date: 2005-01-15
forum: General Help
---

### Post by pseudonym on 2005-01-15
Hello,

I installed Wine using Synaptic but noticed some important parts of it didn't get installed for some reason eg. the all-important ~/.wine directory. So I uninstalled it and decided to build it from source following these instructions - [http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb) (scroll down to bottom).

The build itself worked but the act of doing so has caused a bunch of other files/applications to be deleted in the process. Not being an expert in such matters, I'm at a loss to explain why. 

One thing that got uninstalled was my nvidia-glx driver. I thought it might be just a simple matter of re-installing it, but no. Doing apt-get install nvidia-glx produced the following at the start -

Die folgenden Pakete werden ENTFERNT: (The following packages will be REMOVED)
  firestarter freeglut3 gdm gksu gnome-netstatus-applet gnome-system-monitor
  gnome-system-tools libarts1 libarts1-dev libgksu1.2-0 libgksuui1.0-0 libgle3
  libglu1-mesa libglu1-mesa-dev libglut3 libqt3-mt-dev libqt3c102-mt lsb
  mesa-common-dev mesag-dev mesag3 python-opengl python2.3-opengl
  qt3-dev-tools rss-glx synaptic xbase-clients xmms-qbble xscreensaver-gl
Die folgenden NEUEN Pakete werden installiert: (The following NEW packages will be installed)
  nvidia-glx xlibmesa-gl xlibmesa-glu

Most of the packages listed for removal look pretty damn important so I aborted the install as soon as I saw this message.

Can anyone explain what's going on here? Why is apt-get (and Synaptic) doing this? Is there a way I can fix it? Would uninstalling wine make a difference? I would have tried that already but I'd prefer not to if possible after having gone to all the trouble of building it.

Any help would be greatly appreciated. This is only the second major problem I've had after using Ubuntu for a month (the other was the nightmare of getting my zip drive to work, but that's another story :) ).

---

### Post by Quest-Master on 2005-01-15
Yeah, if you install Wine to use your Windows install, it'll nuke it soon enough.

I know from experience. :(

---

### Post by lockenkeyster on 2005-01-15
I installed wine via apt-get and didn't have any weird installation problems... but it also didn't create ~/.wine. I had to run wine from the command line 

user:~$ wine

and then it created the necessary directories.

Hope that helps!

---

### Post by pseudonym on 2005-01-15
Thanks. I'll remember that when I eventually get things right again. I've a feeling I'm gonna have to re-install Ubuntu, though - I've just lost my X-Server and I suspect a heap of other stuff got corrupted during that wine build/install. :-(

---

