---
title: "How do you change language in (K)Ubuntu post-installation?"
date: 2007-03-11
forum: Desktop Environments
---

### Post by KeeperOS on 2007-03-11
Hi, today I installed Kubuntu on a VM (after Ubuntu, just to check and compare) and just for the hell of it I chose Greek for the system language. After the installation I tried to change it back to English; sure enough, I went to System Setings -> Regional and Language and chose US English as the primary language (simply moved it on top of Greek on the Languages list).

However this only does half the job, it does change some (most?) dialogs and menus back to english but several aspects of the system (including most annoyingly the Konsole Terminal) remain in Greek.

- Is there a way to completely change the system language post-install or do I have to reinstall the OS in order to change that?
**EDIT-_SOLUTION_**_: Found it: One must go under system -> Language Support -> Default Language._
Moving right along to a tougher one and a possible BUG:


- Furthermore, in Ubuntu there is the ability of choosing the system language during Log on (especially useful when different users want to have the language set differently). Is there such an option in Kubuntu?


- Finally, I have searched again and again and I can't find where the hell to choose the key-combo for switching back and forth the different keyboard layouts. Any help on that?
**EDIT-_POSSIBLE BUG_:** Ok, found it but for some weird reason it won't accept "Ctrl+Alt" as the hotkey plus the default (Ctrl+Alt+K) will not work once I'm in Greek (the "Kei" becomes the Greek letter "Kapa" which apparently is not recognized as the hotkey...).
I also noticed that this happens only after I manually select Greece as my language/region (instead of the default selection "Default") and then activate the multiple keyboard layouts (which creates that icon that shows a flag for the active language).
Before that everything was working perfectly. What does that thing screw up?

I know these are a lot but regional customization matters A LOT to non-native English users, even if they speak English...

Thanks!

---

### Post by KeeperOS on 2007-03-13
Bump, please guys, I need you to tell me if there's a way in Kubuntu to choose the language on a per user basis (possibly during log on) like in Ubuntu.


Furthermore could you confirm that the following is a bug?

[I]"**_POSSIBLE BUG_:** - Ok, when I first installed Kubuntu (in Greek) _Alt+Shift_ would cycle between Greek and English layout (with the Scroll Lock led cycling on or off). Everything was working fine. However after I manually selected Greece as my language/region (instead of the default selection "_Default_") and then activated the multiple keyboard layouts (which creates that icon that shows a flag for the active language) 
 for some weird reason it no longer accepted "_Ctrl+Alt_" as the hotkey plus the (new) default (_Ctrl+Alt+K_) will not work once I'm in Greek (the "Kei" becomes the Greek letter "Kapa" which apparently is not recognized as the hotkey...).

What did that thing screw up?"[/I] 

Please tell me so that it can be fixed for the upcoming version...

---

### Post by qyte on 2007-03-19
I have installed ubuntu in English and even though i have included Greek in language support i cannot find where i can change between languages ANYWHERE :mad: 

Can someone tell me what more is there to be done PLEASE???

---

### Post by jbulcher on 2007-03-19
qyte,

I'm pretty sure there is an option to change your language at the login screen, in the lower left hand corner. I'm not sure how permanent it is though.

A more permanent solution: System-Administration-Language support. You can set your default language there, as well as set up supported langages.

I've never used it before, and it sounds like it isn't as thorough as it could be - so good luck with it!

Sorry KeeperOS, I've got nothing. Hope you've found something by now...

---

### Post by qyte on 2007-03-19
well never mind i figured it out. It was xfce that did not have access to keyboard settings so i got back into gnome and solved it ;)
The gnome language indicator though REALLY SUCKS!!! :(

---

### Post by simosx on 2007-04-05
> **qyte said:**
> well never mind i figured it out. It was xfce that did not have access to keyboard settings so i got back into gnome and solved it ;)
The gnome language indicator though REALLY SUCKS!!! :(

You switch languages at the login screen, under options. If your system boots directly to your account (does not ask for a username/password), you need to logout once, change language and login again.

Greek Ubuntu support at 
[http://www.ubuntu-gr.org/Wiki](http://www.ubuntu-gr.org/Wiki)
Mailing list: [https://lists.ubuntu.com/mailman/listinfo/ubuntu-gr](https://lists.ubuntu.com/mailman/listinfo/ubuntu-gr)

---

### Post by simosx on 2007-04-05
> **KeeperOS said:**
> Bump, please guys, I need you to tell me if there's a way in Kubuntu to choose the language on a per user basis (possibly during log on) like in Ubuntu.


Furthermore could you confirm that the following is a bug?

[I]"**_POSSIBLE BUG_:** - Ok, when I first installed Kubuntu (in Greek) _Alt+Shift_ would cycle between Greek and English layout (with the Scroll Lock led cycling on or off). Everything was working fine. However after I manually selected Greece as my language/region (instead of the default selection "_Default_") and then activated the multiple keyboard layouts (which creates that icon that shows a flag for the active language) 
 for some weird reason it no longer accepted "_Ctrl+Alt_" as the hotkey plus the (new) default (_Ctrl+Alt+K_) will not work once I'm in Greek (the "Kei" becomes the Greek letter "Kapa" which apparently is not recognized as the hotkey...).

What did that thing screw up?"[/I] 

Please tell me so that it can be fixed for the upcoming version...

It looks that this issue is specific to Kubuntu.

The Greek Ubuntu team is at
[https://launchpad.net/~ubuntu-l10n-el](https://launchpad.net/~ubuntu-l10n-el)

---

### Post by kingpico on 2007-05-07
hello

well first u have to use a greek xmodmap if u want to write in greek , these can be found in /usr/share/xmodmap

to enable a greek xmodmap use the following code :

xmodmap /usr/share/xmodmap/xmodmap.gr

Usually the modifier key to change language is altgr( the right alt key) 

So to write greek u have to press altgr and type your greek chars. To write in capitals press shift+altgr at the same time,

Hope this will solve the problem. Mine is working fine

---

