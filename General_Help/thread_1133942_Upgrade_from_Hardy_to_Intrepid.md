---
title: "Upgrade from Hardy to Intrepid"
date: 2009-04-23
forum: General Help
---

### Post by BslBryan on 2009-04-23
Hello all.

I have been using Ubuntu 8.04 for a while now, and plan on keeping it for a while.  Of course, sooner or later I'll have to upgrade.  I'm sorry if my question sounds silly, but I'm wondering what exactly is lost when you upgrade.  For example, if I had to do work to get my wireless chipset to work, will I have to do it again?  Will I have to reinstall the drivers for my graphics card to work correctly?  What about the rest of my drivers?  Will I lose the customization that I've worked hard on?  Will my custom login screen still be available?  Will my music and photos, etc. be lost?  Thanks in advance for helping! :)

---

### Post by overdrank on 2009-04-23
> **BslBryan said:**
> Hello all.

I have been using Ubuntu 8.04 for a while now, and plan on keeping it for a while.  Of course, sooner or later I'll have to upgrade.  I'm sorry if my question sounds silly, but I'm wondering what exactly is lost when you upgrade.  For example, if I had to do work to get my wireless chipset to work, will I have to do it again?  Will I have to reinstall the drivers for my graphics card to work correctly?  What about the rest of my drivers?  Will I lose the customization that I've worked hard on?  Will my custom login screen still be available?  Will my music and photos, etc. be lost?  Thanks in advance for helping! :)

Hi and if you plan on upgrading why not wait for the next LTS and then upgrade. :)

---

### Post by Kareeser on 2009-04-23
> **BslBryan said:**
> Hello all.

I have been using Ubuntu 8.04 for a while now, and plan on keeping it for a while.  Of course, sooner or later I'll have to upgrade.  I'm sorry if my question sounds silly, but I'm wondering what exactly is lost when you upgrade.  For example, if I had to do work to get my wireless chipset to work, will I have to do it again?  Will I have to reinstall the drivers for my graphics card to work correctly?  What about the rest of my drivers?  Will I lose the customization that I've worked hard on?  Will my custom login screen still be available?  Will my music and photos, etc. be lost?  Thanks in advance for helping! :)

You'd have to reinstall wireless and graphics card drivers, unless they have been integrated upstream and are installed automatically.

Your data in /home should be fine, and your login screen should stay the same.

---

### Post by limegreenpatato on 2009-04-23
What about application that are installed?  Normally and through wine?

---

### Post by drs305 on 2009-04-23
All of this depends on how you install the next release. If you do it on-line via update manager or apt-get your data and settings, to the maximum extent possible, will be retained, including your added apps and Wine. You may have to reinstall some drivers but not necessarily. Your configuration settings should be retained.

If you do a clean install without a separate /home partition, everything will be overwritten. You would lose all your customizations, added apps, and any data you have stored in /home or anywhere on the / partition. You can prevent this by making a separate /home partition in your current installation. In that case, you would use the LiveCD to install the new version but elect to retain your current /home partition, and *NOT* format it.  You would keep the customized configuration settings normally stored in your /home folder and anything else in your /home folder. You would not keep any extra apps you had installed, although there are commands you can run to save a list of your current apps, which you can then import to a clean install.

---

### Post by limegreenpatato on 2009-04-23
> **drs305 said:**
> All of this depends on how you install the next release. If you do it on-line via update manager or apt-get your data and settings, to the maximum extent possible, will be retained, including your added apps and Wine. You may have to reinstall some drivers but not necessarily. Your configuration settings should be retained.

If you do a clean install without a separate /home partition, everything will be overwritten. You would lose all your customizations, added apps, and any data you have stored in /home or anywhere on the / partition. You can prevent this by making a separate /home partition in your current installation. In that case, you would use the LiveCD to install the new version but elect to retain your current /home partition, and *NOT* format it.  You would keep the customized configuration settings normally stored in your /home folder and anything else in your /home folder. You would not keep any extra apps you had installed, although there are commands you can run to save a list of your current apps, which you can then import to a clean install.


Awesome, thanks.   I haven't decide if i'm going to upgrade yet....maybe wait a few weeks till people start figuring out all the little bugs with the new release.

---

### Post by BslBryan on 2009-04-23
Thanks for all of your replies.  Someone mentioned waiting for the next LTS, and this is something I plan on doing.  I'm perfectly happy with Hardy, at the moment.  :-)  Yes, I always planned on upgrading via apt-get, so I'm glad that most of my data will be retained when the day eventually comes.  I'll back it up before the upgrade, though, just in case.  :-D

---

