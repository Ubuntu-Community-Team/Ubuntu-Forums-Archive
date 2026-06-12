---
title: "Annoying MTP/UMS Sony audio player issues."
date: 2009-04-30
forum: General Help
---

### Post by darweth on 2009-04-30
I've never had trouble with my SONY audio player in any incarnation of Linux pre-Jaunty.  I think the libmtp that shipped with Ubuntu 9.04 was a little messy and I had issues using MTP with my UMS-set audio player.  You know... it boots up as a UMS drag-drop external drive, but you can temporarily use MTP while within an audio player.  This was not working.  Somehow after toying around with the player, I ended up setting it from a default UMS device to a default MTP device.  Now it booted up as a MTP device at every boot up and I could not access it at all.  I upgraded the libmtp from a PPA and the same issue.  I ONCE was somehow able to get it to boot up UMS and it worked normal like it did on previous distros but that was a fluke.

SO what did I do?  I had to take it to work on a Windows XP box to change the default settings from MTP back to UMS (no clue or instructions to be found on how to accomplish this in Linux).  It worked fine.  Tested it out on Windows a few times to make sure it plugged in UMS.  Dreamy.  

I take it home and Linux expects it to be an MTP device once more.  WTF?!  I reset it as UMS.  Are there HAL settings or some device settings I have to wipe?  I had audio players set up to do nothing via default.  Not to open any folder or boot into any programs.  I am lost here.  This SONY Player works fine but is pretty much right now a brick on my Linux OS.  What to do?  What to do?

Thanks.

---

### Post by jordilin on 2009-05-04
Well, libmtp in jaunty uses an old one 0.3.0 which is apparently somewhat screwed.
 
There is a bug raised [https://bugs.launchpad.net/bugs/348287](https://bugs.launchpad.net/bugs/348287) 

I posted a workaround which goes through compiling the latest libmtp available which is 0.3.6. If you are not scared about using command line and you've got quite a bit of experience, then you could follow my workaround in:

[http://jordilin.wordpress.com/2009/05/04/libmtp-and-ubuntu-jaunty-mtp-devices-rhythmbox/](http://jordilin.wordpress.com/2009/05/04/libmtp-and-ubuntu-jaunty-mtp-devices-rhythmbox/)

---

### Post by darweth on 2009-05-04
Yep.  I already updated to 0.3.6.  :)  You are right about the mtp shipping with Jaunty being buggy.  That is why this whole problem began.  I could not connect via MTP short-term with 0.3.0.  The one time my device booted up UMS (freak accident) once I upgraded to 0.3.6, everything worked FINE!!!  But it does not work when the device is default MTP... only default UMS.  Confusing, I know.

I brought the device back to work today and Windows immediately saw it as a UMS (not MTP) device so I am not sure what is going on.  Back on Linux, it defaulted to MTP??  Lol.  Must be a HAL setting saved somewhere.  Probably reinstalling the OS and wiping all configs could fix the problem.  Not sure.  Might just have to roam to Windows pcs and manage the player from there. :/

---

### Post by darweth on 2009-05-04
Omg nevermind.  While I still have that problem with Libmtp 0.3.6 as noted on your blog, unmounted the device and THEN connecting WORKS!!  I will just do that pain in the *** step for now!!!

---

