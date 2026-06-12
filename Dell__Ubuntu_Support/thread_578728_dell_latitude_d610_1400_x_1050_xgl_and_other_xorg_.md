---
title: "dell latitude d610 1400 x 1050 xgl and other xorg related issues"
date: 2007-10-17
forum: Dell  Ubuntu Support
---

### Post by kristofer on 2007-10-17
My primary issue with the dell latitude d610 is the custom resolution. 915resolution doesn't seem to help at all, so I switched from the i810 driver to the intel driver. That worked wonders for performance (ie.. all the beryl stuff worked just great) but the custom resolution still didn't work.

Now I've upgraded to gutsy because of xserver-xgl and compiz and all that stuff.. but xgl is sluggish on my d610. That's not a major problem. I can always switch to another one. But I still can't seem to get that extra screen real-estate working.. any ideas?

I guess natively it should support 1400 x 1050. Anyone have a success story with the special resolution on the d610?

---

### Post by bluedragon436 on 2007-10-19
I am actually fighting with the same thing now...  I upgraded from 7.04 to 7.10 and have been messing around with the settings for over 12hrs, not straight but overall....  Anyways I have an issue with the 3D desktop swap right now, and have not been able to figure that out.  I can switch from desktop to desktop but it just switches there is no effects or anything.  And when I go into the Preferences>Apperance and click on the Visual Effects tab and try to activate the effects I get a message that says: The Composite Extension is not available...  Kind of annoying but I guess I will keep working on that part, but other than that I have no problems with the graphics.

---

### Post by kristofer on 2007-10-19
yeah, the desktop effects work.. albeit xgl slowness, all is well. the custom resolution is more important to me at this point though.

---

### Post by kristofer on 2007-10-19
I've been messing with System->Administration->Screens and Graphics - it's a nice utility that correctly sets the resolution (1400x1050) when I click the test button. So I choose to keep the settings after I see that it finally works. The usual process of logging out and back in occurs, and then it tells me it can't set the resolution?!!?

It just worked upon clicking test!? Any ideas?

---

### Post by kristofer on 2007-10-22
I gave up on xgl, and now I'm using the i810 driver because it has xinerama support. Compiz works really well using the i810 driver, but I still can't set the resolution to 1400 x 1050. I'm running bios A05, so 915resolution isn't really an option. Is there anything else I can do to get the native resolution to work?

---

### Post by rabbito on 2008-01-18
not sure if you got your problem fixed or not but i just got a D610 and it detected the correct 1400x1050 res. Check your usplash.conf file to see what it says. I had to manually go in and correct mine because it was detecting 1280x1024. BTW mine has the intel graphics if that makes a difference. I am thinking of turning visual effects off though because after i log in my load time is not as fast as i would like it to be and that may be because i have it set to Normal effects with the intel graphics. Mine has the 1.73ghz with 2gb ram.

---

