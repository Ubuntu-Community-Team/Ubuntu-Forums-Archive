---
title: "i have 'broken dependencies' and to fix package manager wants to erase ubuntu desktop"
date: 2005-10-29
forum: Desktop Environments
---

### Post by jacknel on 2005-10-29
ok i've been using ubuntu for the last 3 days and so far am liking it for the most part...

i tried to run the upgrade checker (top right hand corner)  but it said  an error had occured and that i had 1 broken package on the system - use the "broken" filter to locate it...

so i run it in packagemanager (looks same as synapse thing)... and this is what it wants to do.....

[i]
gdm will be removed
gksu will be removed
gnome-app-install will be removed
gnome-netstatus-applet will be removed
gnome-system-monitor will be removed
gnome-volume-manager will be removed
hwdb-client will be removed
kaffeine will be removed
kdelibs-bin will be removed
kdelibs4 will be removed
libgksu1.2-0 will be removed
libgksuui1.0-0 will be removed
python-gnome2-extras will be removed
python2.4-gnome2-extras will be removed
serpentine will be removed
ubuntu-desktop will be removed
x-window-system-core will be removed
xbase-clients will be removed
xkeyboard-config will be removed
xsm will be removed
xlibs (version 6.8.2-10.1) will be installed
xlibs-data (version 6.8.2-10.1) will be installed
[/i]

any ideas? i did change the repository to my isp if that makes a dif (mirror.internode.on.net........)

---

### Post by greatshape on 2005-10-29
[QUOTE=jacknel]ok i've been using ubuntu for the last 3 days and so far am liking it for the most part...

i tried to run the upgrade checker (top right hand corner)  but it said  an error had occured and that i had 1 broken package on the system - use the "broken" filter to locate it...
[/QUOTE]
What package is broken? 
Open a shell and typ

sudo apt-get install -f *BrokenPackageName*


regards Steve

---

### Post by jacknel on 2005-10-30
thx greatshape... i ended up uninstalling xine-ui which inturn uninstalled operah and that fixed everything...

curiously though - that command u gave owuldnt work would it because in order for it to be installed it required other things be removed...

---

