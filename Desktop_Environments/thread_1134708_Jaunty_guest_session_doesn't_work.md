---
title: "Jaunty guest session doesn't work"
date: 2009-04-23
forum: Desktop Environments
---

### Post by Tomasino12 on 2009-04-23
I just installed the new Jaunty and wanted to try out the Guest session. All I got was a black screen and I had to restart my PC. It happened for a few times. Maybe one of the problem would be that I'm using a 64bit version. Any suggestions?

---

### Post by dkfroggy on 2009-04-26
Same problem here with a fresh install of Jaunty, 32 bits, ext4, Intel graphics on a laptop. And creating a new user session ends up with the same black screen.
But on another computer (desktop) where I upgraded to Jaunty from Intrepid, kept ext3 and have an Nvidia card, the guest session works flawlessly. 
This computer says "Guest" (in English) in the applet whereas the laptop applet says "session d'invité" in French.
Both systems have French local settings.
Could it be an Intel issue ?

---

### Post by rscarriere on 2009-04-26
I have a laptop with Intel graphics.  I added options to re-enable compiz in Jaunty including this line in my xorg.conf

Option "AccelMethod" "UXA"

When trying to login to a guest session the system would lock up. I removed this line and everything is working again.

Hope that helps.

---

### Post by dkfroggy on 2009-04-26
@rscarriere
Yes, that's it. Thanks a lot.

---

