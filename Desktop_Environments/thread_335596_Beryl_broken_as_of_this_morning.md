---
title: "Beryl broken as of this morning"
date: 2007-01-10
forum: Desktop Environments
---

### Post by jimbo99 on 2007-01-10
I've been using beryl for some time.  It was the main motivating factor in installing ubuntu on this computer.  Since doing so I have begun to use it as my primary machine.

This morning I was prompted that I had updates and the system indicated that the xorg core was updated and that I should install it.

I did this.

After rebooting the computer and invoking beryl-manager the screen goes black, blinking cursor in the upper left hand corner of my screen, the nvidia logo screen pops up, and I'm taken back to the login screen.

I figured since there are settings that need to be in place in the xorg.conf file and the fact that a past update had once wiped those setting out, I went into the xorg.conf file and determined that those setting were in the proper place still.

Essentially, after this update beryl no longer works.  Keep in mind, shy the various updates from beryl that have wrought havoc within beryl, it has been running without any major problems for about 3 months.  Nothing else was changed so there is no coincidence of problem to recent change, except for that of the xorg core component being upgraded.  This update came through the update notification given by ubuntu and not me going out and getting an update from some other web site.

Any suggestions?

---

### Post by nkkromhof on 2007-01-10
You need to reinstall your videocard drivers again after having updated xserver-xorg.

Follow the steps [HERE]("http://www.ubuntuforums.org/showthread.php?t=263851"), listed at Step 2.

---

### Post by liquidflem on 2007-01-10
Same here, i just installed the Xorg updates and the new kernel restricted modules and now beryl kills and causes Xorg to restart. I tried installing/reinstalling beryl with no luck. Im hoping this is fixed soon. Xorg seems to have been untouched.

Are there nightly builds of beryl?

---

### Post by orgyn on 2007-01-10
> **liquidflem said:**
> Same here, i just installed the Xorg updates and the new kernel restricted modules and now beryl kills and causes Xorg to restart. I tried installing/reinstalling beryl with no luck. Im hoping this is fixed soon. Xorg seems to have been untouched.

Are there nightly builds of beryl?

reinstall video card driver

---

### Post by nkkromhof on 2007-01-10
See above ;-)

It's not Beryl that's broken...

---

### Post by jimbo99 on 2007-01-10
> **nkkromhof said:**
> You need to reinstall your videocard drivers again after having updated xserver-xorg.

Follow the steps [HERE]("http://www.ubuntuforums.org/showthread.php?t=263851"), listed at Step 2.

Actually I'm using the latest nvidia drivers from the nvidia website.  I would never think about using anything else.

Nonetheless I'll give it a try.

I can't say I agree, but I am leaning toward the conclusion that it isn't beryl that is broken.  What crosses my  mind is "incompatibility".  Someone somewhere goofed.  But I do know that my desktop manager and nvidia drivers load after the xorg core update, whereas the beryl project does not.

---

### Post by jimbo99 on 2007-01-10
For those following hoping this is their solution--to reinstall the nvidia drivers--the good news is that it does work again, even with the latest drivers downloaded from the nvidia website.

---

