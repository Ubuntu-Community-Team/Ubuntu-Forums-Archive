---
title: "so I want to go back to AIGLX..."
date: 2008-02-27
forum: Desktop Effects &amp; Customization
---

### Post by calman on 2008-02-27
...but I don't know where to begin.  I installed XGL a while ago but now I realized I want AIGLX.  As far as I know, Ubuntu 7.10 comes with AIGLX, so it's somewhere in there (correct?) but not enabled because I installed XGL.  And I'm assuming I do something somewhere in xorg.conf, but I don't know the best way to enable it.  Thanks.

---

### Post by santiagoward2000 on 2008-02-27
> **calman said:**
> ...but I don't know where to begin.  I installed XGL a while ago but now I realized I want AIGLX.  As far as I know, Ubuntu 7.10 comes with AIGLX, so it's somewhere in there (correct?) but not enabled because I installed XGL.  And I'm assuming I do something somewhere in xorg.conf, but I don't know the best way to enable it.  Thanks.

Hi!
To disable XGL, you need to create a file called **disable** in ~/.config/xserver-xgl
Next time you blog in, it should be disabled.
I guess AIGLX should be enabled again, but I'm not sure, because my ATI doesn't support AIGLX.
Good luck!

---

### Post by Melcar on 2008-02-27
Just undo all the stuff you did to install XGL.  Uninstall xgl-server, remove any scripts you might have created, make sure xorg.conf does not have any option that would disable AIGLX.

---

### Post by calman on 2008-02-27
Thanks for the quick response.  How do I check if I'm using AIGLX or XGL?

---

### Post by Melcar on 2008-02-27
XGL usually requires a separate session to work, so if you're not in the XGL session, you're not using it.  To check if AIGLX is on, check xorg.conf, and make sure there are no options referring to AIGLX (like AIGLX *off*).  Unless you specify in xorg.conf, AIGLX will be turned on by default on Gutsy.

---

### Post by calman on 2008-02-27
Alright, I'm almost positive AIGLX is working again, good ol' Compiz is running a bit better and I'm not having some of the same really small problems.  I thought there was a command that told you which one was running, though.  That would be useful...

thanks for the help

**EDIT:**
Apparently when you run Compiz manually ("compiz" in terminal) it should say "checking for xgl".  If it says "not present" you're running AIGLX.  Otherwise, well, you know...

---

### Post by santiagoward2000 on 2008-02-27
> **Melcar said:**
> XGL usually requires a separate session to work, so if you're not in the XGL session, you're not using it.  To check if AIGLX is on, check xorg.conf, and make sure there are no options referring to AIGLX (like AIGLX *off*).  Unless you specify in xorg.conf, AIGLX will be turned on by default on Gutsy.

Actually, that was before. Since Gusty, you no longer need a separate session to run XGL. That's why you now have to create the **~/.config/xserver-xgl/disable** to turn it off.

---

