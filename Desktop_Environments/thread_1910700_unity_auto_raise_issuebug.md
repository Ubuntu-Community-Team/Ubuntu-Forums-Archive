---
title: "unity: auto_raise issue/bug?"
date: 2012-01-17
forum: Desktop Environments
---

### Post by airdelroy on 2012-01-17
I am new to unity and am having an annoying issue with auto_raise.  If you maximize a window (say firefox) and then open 2 smaller windows on top of firefox (say Terminal) so that you can see all 3 windows at the same time.  Then close one of the Terminal windows.  The window directly under the closed window is then auto_raised up, pushing the other Terminal down.

I have focus mode set to sloppy and I believe I have auto_raise disabled (Its not checked in gconf metacity general).  I also have focus_new_window set to smart.

Ideas on how to change this behavior?

thanks,
Aaron

---

### Post by airdelroy on 2012-01-18
I didnt think it would change what Im looking for, but I tried changing focus_new_window to strict from smart.  This did not solve the issue.

Anyone have any ideas?

thanks,
Aaron

---

### Post by airdelroy on 2012-01-19
I cant believe nobody is having this issue.

I have a small finding.  It looks like the window that previously had focus is the window that gets raised.  If I set focus_mode to "click" and click a terminal window before closing the other then the remaining terminal window stays on top.  This is the behavior Im looking for.

I would think that window focus should have nothing to do with autoraise.  But that does not seem to be the case.

Aaron

---

### Post by Frogs Hair on 2012-01-19
I can't reproduce the behavior . If Firefox is maximized and two terminal windows are opened and one of them is closed the other terminal remains above the Firefox window .  If I make Firefox the active window by selecting it then the other terminal goes below the Firefox window . 

To get the the terminal on top again I select the terminal  icon on the Unity panel. For me the active window is always on top . You could check Launchpad to any bugs have been filed .  [https://bugs.launchpad.net/](https://bugs.launchpad.net/)

---

### Post by airdelroy on 2012-01-19
Is your focus_mode "click", "mouse", or "sloppy"?  If I set the mode to "click" I can't show the issue when the mode is set to "click".  Because the previously focused window has to be the other terminal in order to get both terminals above the firefox window.  The problem only happens with the mode set to "mouse" or "sloppy".

thanks,
Aaron

---

### Post by Krytarik on 2012-01-19
I, too, have tested this earlier today with both my Lucid 10.04 system and an Oneiric 11.10 Live ISO, in both running Metacity, of course, and with exact the same settings you've mentioned; and I, too, couldn't reproduce this behaviour, sorry. Like *Frogs Hair*, I suggest searching for possible related bug reports:

[https://bugs.launchpad.net/ubuntu/+source/metacity](https://bugs.launchpad.net/ubuntu/+source/metacity)

Regards.

---

### Post by Frogs Hair on 2012-01-20
> **airdelroy said:**
> Is your focus_mode "click", "mouse", or "sloppy"?  If I set the mode to "click" I can't show the issue when the mode is set to "click".  Because the previously focused window has to be the other terminal in order to get both terminals above the firefox window.  The problem only happens with the mode set to "mouse" or "sloppy".

thanks,
Aaron

I am using default settings and made no configuration changes since installation .

---

### Post by airdelroy on 2012-01-20
> **Krytarik said:**
> I, too, have tested this earlier today with both my Lucid 10.04 system and an Oneiric 11.10 Live ISO, in both running Metacity, of course, and with exact the same settings you've mentioned; and I, too, couldn't reproduce this behaviour, sorry. Like *Frogs Hair*, I suggest searching for possible related bug reports:

[https://bugs.launchpad.net/ubuntu/+source/metacity](https://bugs.launchpad.net/ubuntu/+source/metacity)

Regards.

This is a good idea.  Ill try the live CD and see what I get.  Although I thought I had to install gconf editor to change the metacity settings?  Not sure how to do that on the live CD...

Ill also go through those bugs to see if anything is close to my issue.

Ill post back what I find.

thanks,
Aaron

---

### Post by airdelroy on 2012-01-20
Strange.  I installed gconf editor in the live boot, but I was not able to get mouse or sloppy focus to work when I changed the config.  Nor did autoraise work.  Ill have to do a little digging to get this enabled.

Aaron

---

### Post by Krytarik on 2012-01-20
> **airdelroy said:**
> Strange.  I installed gconf editor in the live boot, but I was not able to get mouse or sloppy focus to work when I changed the config.  Nor did autoraise work.
Maybe because the Live CD is logging you in to the regular Unity, thus using Compiz; not Unity 2D, which is using Metacity? Which would be kinda strange, of course, since you've apparently either decided against running the regular Unity, or just couldn't get it to run with your video setup.

---

### Post by airdelroy on 2012-01-20
Both the installed and live version are running unity-3D

$ echo $DESKTOP_SESSION
ubuntu


I still cant get mouse focus to work in the live boot.  Both gconf editor and compiz config mgmt seem to be in agreement on the focus_mode setting.  Unchecking the click to focus option in compiz mgmt sets the focus_mode to sloppy in gconf editor.  But it still doesnt work.

Wonder what Im doing wrong.

Here is what I am doing.

Boot live CD (try it now vs install)
install gconf editor (and sources associated with this, and compiz mgmt)
open gconf editor
open apps->metacity->general
click on focus_mode and change it to sloppy

and then it still takes a click to focus.

thanks,
Aaron

---

### Post by Krytarik on 2012-01-20
> **airdelroy said:**
> Both the installed and live version are running unity-3D
[..]
I still cant get mouse focus to work in the live boot.  Both gconf editor and compiz config mgmt seem to be in agreement on the focus_mode setting.  Unchecking the click to focus option in compiz mgmt sets the focus_mode to sloppy in gconf editor.  But it still doesnt work.
Then I'd rather only work with CompizConfig Settings Manager than trying to get it working by tweaking the settings of a window manager you aren't actually using, Metacity, that is. ;-)

---

### Post by airdelroy on 2012-01-20
Im not sure how you guys are able to enable focus follows mouse when booting from the live CD.  I think there must have been a bug that got fixed early after the 11.10 release.

I booted from the CD, installed compiz only, and unchecked "click to focus" in the general->general options section.  But I dont get focus follows mouse.

I cant really find anything online that talks to this.

thanks,
Aaron

---

