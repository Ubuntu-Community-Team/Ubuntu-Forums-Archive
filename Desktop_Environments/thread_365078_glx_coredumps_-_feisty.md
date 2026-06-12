---
title: "glx coredumps - feisty"
date: 2007-02-19
forum: Desktop Environments
---

### Post by hanasaki on 2007-02-19
glx is coredumping on glxinfo and any other use of the lib... glx loads fine in the xorg logs (ie: no errors) I have tried both the build from the restricted packages and the install script downloaded from nvidia.com

---

### Post by wilbur.harvey on 2007-03-23
I am having the same problems today.
I am using the latest updates from today.

There appear to be several problems.

1) I had to load the nvidia-glx-legacy to get around a version mis-match. I didn't have to do this 1 week ago.
2) glx seems to be not loading due to a conflict with composite
3) Attempting to disable composite causes X to crash and not run

/var/log/Xorg.0.log says
(EE) GLX is not supported with the Composite extension

I attempted to disable composite by placing this at the end of my xorg.conf file
Section "Extensions"
       Option  "Composite"     "Disable"
EndSection

Without GLX, my cad stuff is VERY slow.

---

### Post by hanasaki on 2007-03-23
Turns out there was a combo of versions on my system.  I had to manually remove a couple conflicting libs/versions and reinstall the drivers.  It all works now.

---

### Post by paul.dorman on 2007-06-26
Hi there,

it would be great if you could put up more details as to how you solved your problem. I have similar and would benefit and appreciate your solution.

Cheers,
Paul

---

### Post by hanasaki on 2007-07-17
Basically... just "find | grep -i X" where X is a pretty unique part of the libs and .so from the install... it showed the same files with different directories/suffixes for more than one version.  I took the simple route of manually deleting all the clashes and reinstalling via the nv install .sh script.... the .deb system rocks.  however I never quite figured out how to use it to build the drivers.... 

Since then the video card died and I just am using the SIS chips set on my mother board so no more NV at the moment.

---

