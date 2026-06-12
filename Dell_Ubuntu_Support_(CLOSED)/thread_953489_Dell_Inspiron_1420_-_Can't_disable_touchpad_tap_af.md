---
title: "Dell Inspiron 1420 - Can't disable touchpad tap after update to 8.10"
date: 2008-10-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jacobwwood on 2008-10-20
Hi all,

I just upgraded to 8.10 beta and since then I have been unable to disable touchpad tap permanently through System > Preferences > Mouse > Touchpad. If I go to the touchpad settings, it shows that touchpad tap is off, even though it is on. If I then turn it on and then turn it off again, touchpad tap will turn off. However, it will turn back on again the next time I reboot or awaken it from suspend.

I was unable to find a similar bug to this one to report, but before I do I thought I'd check here and see if anyone else knew of a solution.

Thanks!

---

### Post by bdusel on 2008-10-23
Same problem.  I am running 8.10 beta on a Toshiba M200 with Synaptics touchpad.

---

### Post by alof8k on 2008-10-24
Just for clarification,

on Dell 1525 (dual booting with Vista SP1), disabling "enable mouseclicks via touchpad" does indeed turn off tap clicking.

---

### Post by clearshot on 2008-10-26
Happens to me too, have to change it everytime.

Using Kernel 2.6.27-7-generic
Dell 1525N
Ubuntu 8.10

I'm not entirely sure, but updates may have fixed it for me. I restarted this morning and didn't have to change the mouse settings.

---

### Post by TheFightForGood on 2008-10-26
I cannot find this setting anymore.  When I first install the beta at the beginning of this week it was in the mouse preferences, but after updates it is not longer there.  Anyone know if it was moved or what the deal is?  I hate this setting...

---

### Post by clearshot on 2008-10-26
The setting is still there for me under Touchpad. Maybe somethings broke and it doesn't detect it as a touchpad?

---

### Post by Denny Johnson on 2008-10-26
When I upgraded my 1420n to 7.10 and then 8.04, I had touchpad issues.
Resolved them w help from here:
[http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Changing_mousepad_settings](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Changing_mousepad_settings)
[http://ubuntuforums.org/showthread.php?t=469639](http://ubuntuforums.org/showthread.php?t=469639)
Hope it helps.

---

### Post by bdusel on 2008-10-26
After updates this week, turning the tap click option on and then off again resolved it for me.  Click remains off with restart as well.

EDIT:  It remains off through reboot, but standby turns the tap back on.

---

### Post by DGMcCloud on 2008-11-06
There is a similar issue with 'vertical scrolling' and suspend. I have turned off vertical scrolling on my Dell D820. However, after the machine resumes after a suspend, the vertical scrolling is enabled again (although the option is not on on the configuration screen).

Also, my mouse acceleration speed resets to default after a suspend.

---

