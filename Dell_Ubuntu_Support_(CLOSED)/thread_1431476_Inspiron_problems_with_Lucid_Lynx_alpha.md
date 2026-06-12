---
title: "Inspiron problems with Lucid Lynx alpha"
date: 2010-03-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Squatter on 2010-03-16
I have an old Inspiron 510m laptop (Intel 855GME graphics, Intel 2200 wireless 1.25Gb RAM).  I use this as a general surfing machine AND as my Ubuntu test environment so I am patient with it.  Currently I have problems with the Lucid Lynx update I did a week ago.  Everything was fine with Jaunty (9.04) but under Karmic (9.10) I could not get wireless to work.  It would see all of the available routers in the area but could NOT connect with WPA or WPA2.   It was fine with NO encryption (ie open).

It was annoying me to have to use an ethernet cable so decided it was time to try Lucid to see if that fixed the issue.  I ran the upgrade from the Synaptic graphical interface.  On reboot, the system appears to freeze and end up with a blank screen (no graphics/splashscreens at all).  I can run recovery mode with no apparent problems and have done a few "dpkg" updates from the text menu there without issue.  I have also used the text-mode aptitude app to re-install the entire X and Gnome environments.  No change.

If I select "resume boot" in the recovery mode text menu, I get a one line text response "rc-init ..." then freeze.  The text terminals (Alt-F1 to F6) all work fine.  And if I type "startx" in any of these, I get the same frozen blank screen result.  There seems to be no evidence of any left-over X/Gnome processes or any problems logged in any log file.

I know that the ultimate solution may be a complete re-install but as it is a test environment, I wish to understand what went/is wrong.  I assume the X build is broken on the 855GME but I suppose it could be an xorg.conf issue.  Any ideas what next to try or where to look ?

---

### Post by mikewhatever on 2010-03-18
Take a look at the Testing subforum. [http://ubuntuforums.org/forumdisplay.php?f=377](http://ubuntuforums.org/forumdisplay.php?f=377) That is currently the best place to discuss Lucid.

---

### Post by Squatter on 2010-03-22
Patience was the key.  When the Lucid Beta was released, I did a re-install & graphics is fine.  Still problems with WPA and WPA2.  Windows and OSX connect fine.

---

