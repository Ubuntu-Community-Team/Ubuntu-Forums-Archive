---
title: "Ubuntu Herd 2 -- i386 Desktop CD (manual partitioning)"
date: 2007-01-11
forum: Development CD/DVD Image Testing
---

### Post by pochu on 2007-01-11
Test case type: [FONT=mon]**Ubuntu Herd 2 -- x86 Desktop CD**[/FONT]**, manual partitioning**
Image ID: **<e.g. 20070111**
Date of testing: 2007-01-11
md5sum confirmed: Yes
Pass/Fail: PASS 
Bugs identified: #78801

Regards
Pochu

---

### Post by tormod on 2007-01-11
Test case type: [FONT=mon]**Ubuntu Herd 2 -- i386 Desktop CD**[/FONT]**, manual-partitioning**
Image ID: **20070111.1**
Date of testing: 2007-01-11
md5sum confirmed: Yes
Pass/Fail: PASS 
Bugs identified: [#78868]("https://launchpad.net/bugs/78868") Ubiquity screws up display, but this is fixed by a console switch and back.

[#59618]("https://launchpad.net/bugs/59618") Safe Graphics Mode is broken, IMHO a blocker.

(For once Ubiquity worked on my 256-32=224 MB laptop in a full Gnome session!)

---

### Post by spd106 on 2007-01-12
Test case type: Ubuntu Herd 2 -- i386 Desktop CD
Image ID: 20070111.1
Date of testing: 2007-01-12
md5sum confirmed: Yes
Pass/Fail: [COLOR="Red"]Fail[/COLOR]
Bugs identified: [#78868]("https://launchpad.net/bugs/78868") Ubiquity screws up display. 
For my laptop the ctrl+alt workaround has no effect, the only way to clear it is to restart X. I can't see enough of the window to proceed except by tabbing guesswork, so install is impossible. I have the ati rage lt pro agp-133 integrated graphics chip.

I also have [#76294]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/76294")

---

### Post by KingArthur10 on 2007-01-12
Test case type: Ubuntu Herd 2 -- i386 Desktop CD
Image ID: 20070111.1
Date of testing: 2007-01-12
md5sum confirmed: Yes
Pass/Fail: Fail
Bugs identified: #47768 (if I identified things correctly)

The macine will not boot up after selecting to boot to the desktop for install.  It gives me the error "/bin/sh : can't access tty : job control turned off"

---

### Post by rsambuca on 2007-01-12
Test case type: Ubuntu Herd 2 -- i386 Desktop CD
Image ID: 20070111.1
Date of testing: 2007-01-12
md5sum confirmed: Yes
Pass/Fail:  Fail
CD checked for defects:  passed
Bugs Identified:  [#78868]("https://launchpad.net/ubuntu/+source/ubiquity/+bug/78868")

---

### Post by pochu on 2007-01-12
> **rsambuca said:**
> Pass/Fail:  I don't know to what you are referring here.

If you have been able to install the system without important/critical problems.

Regards
Pochu

---

### Post by rsambuca on 2007-01-14
Now passed:  console switched and back to finish installation.

---

### Post by kristjans on 2007-01-14
Test case type: Ubuntu Herd 2 -- i386 Desktop CD
Image ID: 20070111.1
Date of testing: 2007-01-13
md5sum confirmed: No test
Pass/Fail: Pass
Bugs identified: None


**Comments:**
Still the same problems as in the previous Ubuntu release - no widescreen resolution before installing 915resolution, and there's no decent wireless connection manager (have to install networkmanager separately).

Also the laptop indicator that's supposed to show the volume/brightness levels on the top left of the screen gets corrupted and replaces the cursor.

And when you boot up Firefox up, it still says "Welcome to Ubuntu 6.10, Edgy Eft!", while in "About Ubuntu" it says "Thank you for your interest in Ubuntu 7.04 - the Feisty Fawn - released in April 2007".

---

### Post by pochu on 2007-01-14
> **kristjans said:**
> Test case type: Ubuntu Herd 2 -- i386 Desktop CD
Image ID: 20070111.1
Date of testing: 2007-01-13
md5sum confirmed: No test
Pass/Fail: Pass
Bugs identified: None


**Comments:**
Still the same problems as in the previous Ubuntu release - no widescreen resolution before installing 915resolution, and there's no decent wireless connection manager (have to install networkmanager separately).

Also the laptop indicator that's supposed to show the volume/brightness levels on the top left of the screen gets corrupted and replaces the cursor.

And when you boot up Firefox up, it still says "Welcome to Ubuntu 6.10, Edgy Eft!", while in "About Ubuntu" it says "Thank you for your interest in Ubuntu 7.04 - the Feisty Fawn - released in April 2007".
For resolution, wait until Xorg 7.2 is released.

Thanks for testing and reporting!
Pochu

---

