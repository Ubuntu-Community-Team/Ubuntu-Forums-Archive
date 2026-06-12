---
title: "Stuck at low graphics mode after installing AWN"
date: 2008-03-21
forum: Desktop Effects &amp; Customization
---

### Post by mario2409 on 2008-03-21
I am currently in a HP dv2418nr laptop, I installed the video drivers using envy (nvidia drivers) and then I had the great idea of installing avant-window-navigator.

After installing, everythingw was working fine, but I had to restart and once I rebooted my resolution was stuck at 640x480.

I already tried uninstalling AWN, didn't work.  Then I tried uninstalling and installing the nvidia drivers over and over again and still no luck.  Any help?

*edit: I fixed my bad grammar... or some of it :(

---

### Post by mattk132 on 2008-03-21
Run this command (without quotes):  sudo dpkg-reconfigure xserver-xorg.  This will give you a nice little text based installer to reconfigure X.  But, about Awn.  You need to have compiz-fusion installed to run this.  Make sure xserver-xgl is installed in synaptic.  After that make sure the effects settings are set to higher than none.:)

---

### Post by mario2409 on 2008-03-21
Worked, thanks :) and regarding compiz, I do have it installed.

---

### Post by mario2409 on 2008-03-22
well, it turns out the problem is back again.  So I decided once I got every back to normal, I installed AWN again, restarted but no problem.  It was fine for the past day or so, but out of nowwhere it I am back at stuck at low graphics mode.

I uninstalled AWN, uninstalled drivers, reinstalled drivers, and did the command that you mentioned, and works again.  So is AWn screwing everything up? or whats the deal :(

---

### Post by moonbeam on 2008-03-23
> **mario2409 said:**
> 
I uninstalled AWN, uninstalled drivers, reinstalled drivers, and did the command that you mentioned, and works again.  So is AWn screwing everything up? or whats the deal :(

I can say with a very high degree of certainty that it is not AWN causing the issue.  I could be wrong but  I really don't think so.

---

### Post by durand on 2008-03-23
I have a feeling that it's displayconfig-gtk causing the problem....but I'm not sure.

---

