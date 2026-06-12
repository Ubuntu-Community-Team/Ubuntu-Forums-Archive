---
title: "Still Shouldn't Update Beryl (ATI)?"
date: 2007-06-12
forum: Desktop Effects &amp; Customization
---

### Post by monkeyridesllama on 2007-06-12
Hi, I got Beryl working fine with the [Ubuntu Guide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty"), but it says not to update Beryl automatically.  The little update icon is starting to drive me batty.  

What should I do?

---

### Post by BeardlessForeigner on 2007-06-12
If you install Beryl with AIGLX and an ATI card following this guide (as I did), you can use the updated Beryl versions: [http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)
If you have Beryl installed with flgrx and XGL, you can lock your Beryl version in Synaptic Package Manager by clicking on the individual packages and selecting Packages>Lock version in the menu. There is also a configuration file you can add packages to that will cause them to be skipped but I can't remember where this is atm.

Edit: You said you used the Ubuntu Guide. Its recommended method for ATI cards is with open drivers and AIGLX (in fact its the same as the guide I linked to). If thats the case you dont need to worry about not updating.

---

### Post by Karl S. on 2007-06-12
Try this too
sudo aptitude hold beryl

You can also go to synaptic > settings > software sources > third-party software and unclick beryl

---

