---
title: "Several issues with Ubuntu and Unity, including non-working dialog buttons"
date: 2011-05-01
forum: Desktop Environments
---

### Post by Surlent777 on 2011-05-01
This upgrade has not been very kind to me.

Everything seemed to have gone fine, and then I noticed some very strange things happening. I tried a fresh reinstall and things seemed fine, and now things are once again not fine and I'm not sure what the culprit is, although for some of it I suspect some glitch between Unity and Compiz.

More specifically, I notice the following:

1. The system tray is gone. Hello captain obvious, yeah. Thing is, as documented so graciously at OMG! Ubuntu!, it still exists, but only for certain applications, i.e. Skype, and more to the point, one can whitelist any other apps of their choosing. For me, that'd be Artha (a dictionary/thesaurus) and gnome-gmail-notifier. However, upon adding those two to the whitelist and logging out/in I notice that it is entirely impossible to click the tomboy icon or the battery indicator icon (this is a laptop) without first clicking the mail, sound, or wireless icon first, and then moving the cursor over to it. This is kind of retarded. Resetting the whitelist to the initial settings immediately fixes this. Is there any possible workaround?

2. Adjusting most Compiz settings makes the top bar unusable until logged out/in. This is very annoying. Probably not fixable for a normal user, but bears mentioning.

3. When a window is spawned about halfway down the screen or more, the dialog buttons, i.e. OK/Cancel will absolutely refuse to work until the window is moved (direction may not matter) or you mouse over a very particular part of the button, highlighting it. This seems to strike somewhat at random. It did not seem to occur initially, so I suspect changing a Compiz setting may have done this. I have changed a few settings, those being enabling "Additional Animations", "Bicubic Filter", "Titlebar Information", "Resize Information", "Scale Add-ons", "Scale Title Filter", and adding a lower-left corner action for Scale itself. I also changed the Unity launcher size, but the bug started before I did that.

**EDIT: Turning off Bicubic Filtering seems to have resolved this...or so I thought. I've seen it crop up a couple of times now.** Notably on the theme window.

4. Related to the above, and affecting both of my web browsers (FF and Chromium), sometimes the page seems to somewhat freeze, not responding to the scroll wheel until the scroll bar is manually adjusted, and sometimes links lower on the page won't work until they've been moved up on the page, similar to the dialog boxes noted above.

**EDIT: Turning off Bicubic Filtering seems to have resolved this...or so I thought. I've seen it crop up a couple of times now.** I just changed themes to Orta and it seems to act up more. Or is that just my imagination? That goes for the above EDIT too.

5. Every time I log in I'm spammed by four or five dialogs begging for my keyring password. The option to keep it forever, as opposed to dropping it after a set time or upon logout, is grayed out, making me very unhappy. Is there a way to change that? It seems to ask for it on behalf of the network (I already made the network "available to all users") and possibly gwibber. It's hard to say.

**EDIT: Fixed by deleting default keyring and when prompted to recreate it by Gwibber set it to a blank password.**

6. Most themes, like Orta, display a black triangle in the lower-right hand corner of windows. Is there a way to remove this?

**EDIT: Seems to go away after re-opening the windows.**

7. Code::Blocks has trouble re-drawing when scrolling down due to, apparently, the strange Ayatana scrollbars, particularly the horizontal one. Is there a way to black-list this program, as was done with Firefox and gnome-terminal?

**EDIT: Worked around by uninstalling the new scrollbars (Search Synaptic for "scrollbars", uninstall the two packages)**

Hardware-wise, it's a Samsung NP-QX410, i5 processor, 64-bit OS, 4GB RAM, a touchpad that doesn't work under Linux (thinks it's a ps/2 mouse), and a half-Intel/half-Nvidia graphics card that doesn't seem to tell me much about itself; only the Intel side works properly under Linux and NVidia has no plans to support this monstrosity.

This is all very frustrating, and makes for a bad impression, to say the least. Not that I'm new, but since these are reproduceable, I'm probably not the first one to take note of them. Any advice on any of these would be greatly appreciated.

---

### Post by locazoo on 2011-05-02
Same issue here... i'm really mad about this, it's a pain in the... It's like there are 2 invisible horizontal lines (or rectangles), one thinn at about 250 px from top, 8/10px height, and another at.. let's say 600px from top, 32px height +/-. And the 2nd it's just in there area where dialogs buttons are... it's really anoying to not be able to click them untill wrap the window arround...

PD: I'm not using Unity, i'm using ubuntu classic, running compiz and plugin extras. I also noticed that there's a process called unity-window-decorator running, why's that?...

---

### Post by locazoo on 2011-05-02
> **Surlent777 said:**
> 
6. Most themes, like Orta, display a black triangle in the lower-right hand corner of windows. Is there a way to remove this?


I'm using Orta too... i don't see any black triangle in there.. Try using a different icon pack?

---

### Post by Surlent777 on 2011-05-02
Well, I hadn't had time to update my post yet (I'll go back and do so after this) but for what it's worth I was able to fix the scrollbar related problem by simply uninstalling it-- search Synaptic for "scrollbar" and remove the two packages that are installed. Reboot after to make sure all instances of it are gone. As for the buttons not working, I've found that for no understandable reason turning off Bicubic Filtering has worked wonders. Also got rid of another bug I noticed where after leaving the screensaver (or at least GLMatrix) on for a while the screen went crazy. So far no more freezing in Firefox or non-responsive buttons, so I hope that did it.

---

### Post by Surlent777 on 2011-05-02
> **locazoo said:**
> I'm using Orta too... i don't see any black triangle in there.. Try using a different icon pack?

No dice. Still shows that big black triangle. You can see it in the previews for almost every single theme, though on a fresh install the default themes didn't suffer from this. Orta, however, definitely still does.

EDIT: Oddly enough, now it's working. I guess I had to close the open windows first.

---

