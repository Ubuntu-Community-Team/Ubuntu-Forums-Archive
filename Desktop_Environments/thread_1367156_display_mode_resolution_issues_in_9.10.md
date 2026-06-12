---
title: "display mode resolution issues in 9.10"
date: 2009-12-29
forum: Desktop Environments
---

### Post by bbneo on 2009-12-29
First, the motivation... I plan to use Linux for doing my taxes this year, and I think that TurboTax's online version should work fine for that, *but* it seems to require a newer (3.5+) version of Firefox and 1024 x 768 resolution to work properly.

I have installed Ubuntu 9.10 on one of my machines, but I have a niggling display mode switching issue with it.  After about the second boot (from working correctly... can't remember what I've done exactly to get it to work), the display mode options get locked into 800x600 at best (with a refresh rate of only 60Hz).  I have hacked some with the /etc/X11/Xorg.conf files (?), but can't get this problem solved consistently.  To use TurboTax online, I think you will probably need 1024 x 768 resolution... although their site says that 800x600 is minimum, I have tinkered with it some, and some of the buttons on the screen at Turbotax online don't display at 800 x 600.

Does anybody have a some suggestions about fixing this?  I suppose if I understood how to login to a command line and start or restart the gdm (?) from there (I use Gnome), that might help.  

To be fair, there is one more little twist... I run this machine and another one through a KVM switch into a 19" Samsung monitor.  If I login from with the Ubuntu machine and leave the KVM pointed at it, the login fails, because Ubuntu seems to have some problem setting the display... it just returns to the login screen... at proper full resolution, btw.  

To login, I have to enter my password, hit enter, and then switch the KVM focus to the other machine, and then Ubuntu will login successfully under 800x600 resolution. 

If you've read this far, thanks for your patience and any suggestions.  My other option might be to install something else on that machine that supports Firefox 3.5 or better... maybe a recent release of Debian or fedora 11 or 12.  

Thanks.

---

