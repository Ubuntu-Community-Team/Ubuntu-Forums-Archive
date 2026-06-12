---
title: "Firestarter toolbar problem"
date: 2005-04-12
forum: Desktop Environments
---

### Post by Simian on 2005-04-12
I hope this is the right forum.
Yesterday I installed firestarter. It's a great program that seems to be working well. However I was playing around with it and I detached the toolbar. My problem is that it won't re-attach. I know this sounds like a pet hate rather than a major problem but it is driving me nuts. Not just because it looks so stupid having the menus floating a few inches away from the application but just because it _shouldn't_ be lke that.

I would be very grateful if someone could advise me. I've tried uninstalling and re-installing but somehow it remembers previous settings.

---

### Post by Simian on 2005-04-12
Or could anyone tell me how to remove every trace of an application. So that when I re-install the program it wont remember how it was previously set up. Because when I re-install Firestarter it keeps all of it's previouse setting, namely the floating toolbar that won't re-connect to the application.

Thanks in advance.

---

### Post by soul_rebel on 2005-04-12
you can select to uninstall completely a package from synaptic. Something will still remain in the home dir of users who lauched that app. It is usually a hidden dir or file like ~/.program. I am not sure where firestarter settings are, but this is the norm for other apps.

---

### Post by Simian on 2005-04-13
[QUOTE=soul_rebel]you can select to uninstall completely a package from synaptic. Something will still remain in the home dir of users who lauched that app. It is usually a hidden dir or file like ~/.program. I am not sure where firestarter settings are, but this is the norm for other apps.[/QUOTE]

Thanks for the advice soul_rebel. I'll check the hidden files in my home directory.

---

### Post by mallow40 on 2005-05-27
I had this exact same problem, and found that there is only a one-pixel high area that will allow you to grab the floating toolbar.

place your mouse so that the very tip of the pointer is right on the last pixel at the top of the toolbar.  too low, and you'll select the "preferences...etc" menu, too high and you'll be clicking outside of the box.  just right and when you click you'll get a hand, and then just drag it back on to firestarter.

i suggest doing it with no other windows behind it, or else it gets all screwing trying to mount it to other windows besides firestarter.

good luck :)

---

### Post by stepore on 2005-05-27
[QUOTE=Simian]Thanks for the advice soul_rebel. I'll check the hidden files in my home directory.[/QUOTE]
 ya - except be sure to check the /root/ home directory because that's where the .firestarter directory would be, since you have to be root (sudo) to use it. delete the config file inside and it should create a new one when you next launch firestarter.

---

