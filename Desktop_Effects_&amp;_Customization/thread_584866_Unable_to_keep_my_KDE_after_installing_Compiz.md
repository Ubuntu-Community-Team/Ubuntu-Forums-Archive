---
title: "Unable to keep my KDE after installing Compiz"
date: 2007-10-21
forum: Desktop Effects &amp; Customization
---

### Post by ryan20c on 2007-10-21
I have recently upgraded to Gutsy and installed Compiz.  I followed the How to at [http://kevin.vanzonneveld.net/techblog/article/upgrade_to_ubuntu_gutsy_with_compizfusion/](http://kevin.vanzonneveld.net/techblog/article/upgrade_to_ubuntu_gutsy_with_compizfusion/) and was able to get the desktop effects to work.  When I ran this install, I lost the title bar of all of my apps.  I ran kde-window-decorator --replace which brings everything back but it locks up on my terminal with

ryan@laptop1:~$ X Error: BadDevice, invalid or uninitialized input device 158
X: user not authorized to run the X server, aborting.
ryan@laptop1:~$ kde-window-decorator --replace
X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device


As soon as I close the terminal I lose everything again.  Any Ideas would be great.  Just a note....

I only have 4 desktops enabled but my desktop shows 16.  No idea....

---

