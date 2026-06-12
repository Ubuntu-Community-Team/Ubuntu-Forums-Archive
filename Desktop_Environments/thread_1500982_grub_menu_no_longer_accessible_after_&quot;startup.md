---
title: "grub menu no longer accessible after &quot;startup manager&quot;"
date: 2010-06-03
forum: Desktop Environments
---

### Post by binarypill on 2010-06-03
recently, i used startup manager to change the grub menu timeout from 10 to 0 as i wanted to boot directly to ubuntu instead of having the menu show at boot time (i have a dual boot setup, Ubuntu/Windows).

the problem came up when i wanted to access windows. i used startup manager again to change the timeout back to 10. it did not work anymore. although the menu does show, it only happens for an instant and i cannot access it.

things i have tried:

[LIST=1]
[*]discarded startup manager
a little too late, i guess but i used the cli onward after this fiasco

[*]changed GRUB_TIMOUE in /etc/default/grub
i've changed this from 10 to 20 to 1000 and nothing has worked. i did an "update-grub" after each change in /etc/default/grub too.

[*]changed GRUB_HIDDEN_TIMEOUT
i've read that this does not apply to my setup since i have a dual boot setup but i did it anyway. just in case. it does nothing

[*]changed GRUB_HIDDEN_TIMEOUT_QUIET
same with GRUB_HIDDEN_TIMEOUT, i did this as well. did not help either.

[*]reinstalled both OS's
a last resort move which i expected to work but did not. an interesting thing is that i formatted my / partition which should have removed all previous grub configuration files. my /home partition, on the other hand, i did not change. is there a grub configuration file located in the /home partition? i suspect there is since the grub configuration did not change after the reinstall
[/LIST]

help, anyone? :)

---

### Post by mrinehart93 on 2010-06-03
If you're looking to completely nuke the drive and remove every trace of GRUB so that you can start over, do this (note, it may take awhile):

1. Boot into a Windows DVD
2. Go to the repair installation part of it
3. Open a command line
4. Type this:
a. diskpart.exe
b. sel disk 0
c. clean 

Note that you will lose all your data on the drive if you do that.

---

### Post by binarypill on 2010-06-03
> **mrinehart93 said:**
> If you're looking to completely nuke the drive and remove every trace of GRUB so that you can start over, do this (note, it may take awhile):

1. Boot into a Windows DVD
2. Go to the repair installation part of it
3. Open a command line
4. Type this:
a. diskpart.exe
b. sel disk 0
c. clean 

Note that you will lose all your data on the drive if you do that.

that's a bit too drastic for me. i just did a reinstall and all that. i suspect it's just settings that i missed or something. could be a grub bug too, which means just a bit more waiting for a fix (hopefully :) )

any other ideas?

---

### Post by wilee-nilee on 2010-06-03
Is this a wubi install?

---

### Post by binarypill on 2010-06-03
> **wilee-nilee said:**
> Is this a wubi install?

no, its a multi-partition dual boot install

i finally got it fixed, though i am not very sure how i did it. here's what i did.

[LIST]
[*]put double quotes ("") around the value in GRUB_TIMEOUT
-i've done this before but it didn't work then.


[*]added GRUB_DISABLE_OS_PROBE and set it to true
-i've also done this before and it did not work too


[*]renamed /usr/share/default/grub to /usr/share/default/grub.bak
-this i have not done before and i am strongly suspecting this did something. or not, i'm not sure. i'm a n00bie and everything i did was just hit and miss up to this point.


[*]removed the boot password check on my laptop
-i have my laptop setup to ask for a password before booting. i disabled that. that was not my original intention, actually. i read in a post about enabling "usb legacy support" because grub can sometimes not detect "shift key" presses if you have a usb keyboard (i am on a laptop). it turns out i already had that enabled and, on the way out of the bios setup, i just disabled the boot security option to make restarts quicker.
[/LIST]

the first time i finally got the grub menu, the windows boot option was not there (windows 7, btw). so i went back to /etc/default/grub and set GRUB_DISABLE_OS_PROBE to true. after that, the menu was still there and windows was selectable!

whooh!

---

### Post by binarypill on 2010-06-07
figured it out. it seems that, if i set a bios password on my laptop when the laptop starts, the grub menu won't show or will show but will only flash on the screen for an instant. the password is that is set is for booting the laptop, not for the bios setup. with the password check on, grub menu is inaccessible. without the password check, everything is normal.

---

