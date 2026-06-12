---
title: "feisty and compiz - settings greyed out"
date: 2007-10-27
forum: Desktop Environments
---

### Post by andytof47 on 2007-10-27
Hi htere,

Just installed compiz fusion (after successfully running beryl for ages) and I have fired up te compiz settings manager but unfortunately all my settings are greyed out on the manager and even worse compiz is not workin, it just looks like metacity is working....


any help???


cheers

---

### Post by ohzopants on 2007-10-30
You may have to explicitly enable compiz.  You can do this from the Visual Effects tab of the Appearace Settings dialog (System -> Preferences -> Appearance).

---

### Post by Sandwalker on 2007-11-01
All my Compiz options are greyed out as well; I was experimenting with settings, and the next time I started CompizConfig all the options were disabled.  It doesn't matter whether I have 'Normal', 'Extras' or 'Custom' selected; all are disabled.

I'm using Ubuntu 7.10 on a Compaq Presario 2418AU laptop with an ATi Radeon Xpress 200M.  I'd really appreciate a solution to this problem.

---

### Post by CMM on 2007-11-01
I had to jump through some hoops to get Compiz Fusion to run the way I wanted it to with my ATI Radeon Mobility x1400.  I kept all the information that helped me bookmarked, but unfortunately the laptop is at home.  I can try to post those later if you still need help.  However, I can tell you that I had to setup fglrx  and the ATI drivers manually.  Then, I had to set the set the Desktop effects to Custom and set up the Compiz effects the way I wanted them.

Try this:
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

Re/installing the latest ATI drivers from ATI's site and following that Wiki might fix your problem.

Edit: I did this after I completed a fresh Gutsy install.

This could also be helpful: [http://ubuntuforums.org/showthread.php?t=585045](http://ubuntuforums.org/showthread.php?t=585045)
I actually have Composite set to 0, but I also have Composite set to "Enabled" as well.  Setting it to "Disabled" and 1, or any combination except "Enabled"/0, seemed to break desktop effects for me.

---

