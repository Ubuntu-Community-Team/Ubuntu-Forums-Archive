---
title: "Accidentally removed sound menu from panel"
date: 2010-10-13
forum: Desktop Environments
---

### Post by Nicondrio on 2010-10-13
I accidentally removed the sound menu from my panel bar in Ubuntu 10.10. I did manage to find some solutions to get the sound volume applet in place, like it was in previous Ubuntu versions, but I do obviously prefer the new sound menu in place. Does anybody know how I can get it working again? Thanks for helping me out!

---

### Post by renzokuken on 2010-10-13
is it not just right clicking on the panel..... select Add To Panel and selecting "Notification Area"

---

### Post by Nicondrio on 2010-10-13
No sorry, that doesn't work since the notification area is still present. Somehow I just disabled or deleted the sound menu. I wanted to remove a different applet using right-click and "remove from panel", but somehow I just made the sound menu disappear. Rebooting didn't help by the way.

---

### Post by Frogs Hair on 2010-10-13
You can drag the sound icon from the preferences menu to the panel or add indicator applet from add to panel menu.

---

### Post by Nicondrio on 2010-10-13
Dragging the sound icon to the panel is giving me just a shortcut (or launcher) to the sound preferences menu, but that doesn't give me back the original Ubuntu 10.10 sound menu. The one which integrates with applications like Rhythmbox. It's a decent alternative, but not the real deal.

---

### Post by sanderd17 on 2010-10-13
I don't think the sound menu is in the notification area anymore. I believe its a separate applet. If you right-click and add to panel, do you see anything sound-ish, add it if you see it.

---

### Post by Nicondrio on 2010-10-13
No sound-ish applets in my add to panel menu:
Custom Application Launcher, Application Launcher..., Brightness Applet, Character Palette, Clock, Connect to Server..., CPU Frequency Scaling Monitor, Dictionary Look up, Disk Mounter, Drawer, Dwell Click, Eyes, Fish, Force Quit, Indicator Applet, Indicator Applet Session, Inhibi Applet, Invest, Keyboard Accessibility Status, Lock Screen, Log Out..., Main Menu, Menu Bar, Notification Area, Pointer Capture, Remote Desktop Viewer, Run Application..., Search for Files..., Separator, Show Desktop, Shut Down..., Sticky Notes, System Monitor, Terminal Server Client Applet, Tomboy Notes, Trash, User Switcher, Weather Report, Window List, Window Selector, Workspace Switcher

---

### Post by SantaFe on 2010-10-13
Have you tried opening Nautilus & looking in /usr/bin?  Looked in there & found gnome-volume-control-applet.  Clicked on it & got Just the volume Control Icon on the taskbar.  

At least now I can get rid of the Indicator App now. :)  Now to figure out how to get it to load on re-boot.  :)

Forgot to add, that this was on a system that had 10.04 before updating to 10.10.

---

### Post by Nicondrio on 2010-10-13
Very nice, I did manage to get the standard volume control in place using this method (don't know if it's permanent yet), but not the advanced menu. Right now I've only got a simple slider, like in Ubuntu 10.04

---

### Post by SantaFe on 2010-10-13
I just went to System/Preferences/Startup Applications &  in the Startup programs tab clicked the ADD button & it let me fill in the info.  Rebooted & it was still in the toolbar.  You can still right click on the icon to Mute or set Sound Preferences. :)

---

### Post by Nicondrio on 2010-10-16
Yes, that is the way to launch it every time (otherwise you'll have to re-run it after rebooting) but the problem remains that it's still the volume slider and not the menu like in Ubuntu 10.10. Like you, i've also upgraded from 10.04 but the first reboots it still gave me the new sound menu, only because I accidentally deleted the menu it stoped showing up.

---

### Post by titoaii on 2010-10-17
Hi!

I had the same problem. It seems difficult to resolve but it isn't.
Just right click over the panel. select add to panel and add the  (i don't know the exact name in English but in Spanish is Miniaplicación de indicadores) Mini-applet of indicators or something similar.

I hope this could help.

Regards!

---

### Post by dummy910 on 2010-10-17
> **Nicondrio said:**
> I accidentally removed the sound menu from my panel bar in Ubuntu 10.10. 

Right-Click Panel-Bar>**Add-To-Panel**
-then-
Double-Click **Custom-Application-Launcher**(field)
-then-
Name = **gnome-volume-control-applet**
-then-
Command = **gnome-volume-control-applet**
-then-
Click Icon(top left), change to **gnome-volume-control.png** of the theme folder your currently using
-then-
Click the **Ok-Button**(lower right)

That's it, _please mark as **Solved**_ ;)

---

### Post by Nicondrio on 2010-10-18
It's a better fix, but still not the real deal. This solution gives me an icon to start the basis volume slider. Is it possible to get the same solution working with the sound menu from ubuntu 10.10?

---

### Post by dummy910 on 2010-10-18
> **Nicondrio said:**
> **_It's a better fix, but still not the real deal. This solution gives me an icon to start the basis volume slider._** Is it possible to get the same solution working with the sound menu from ubuntu 10.10?

Odd, as my results prove to be the real deal on the 2 machines I did using the above fix just moments prior to me posting the fix...

I must be missing something :confused:

---

### Post by Nicondrio on 2010-10-18
Well, maybe I'm having a more thorough problem. I'll manage using this solution, but I think I'll just reinstall when 11.04 comes out, solving all problems.

If anybody has a different solution, please reply so I can try it out.

---

### Post by nicholasbgr on 2010-10-20
> **titoaii said:**
> Hi!

I had the same problem. It seems difficult to resolve but it isn't.
Just right click over the panel. select add to panel and add the  (i don't know the exact name in English but in Spanish is Miniaplicación de indicadores) Mini-applet of indicators or something similar.

I hope this could help.

Regards!
> **Nicondrio said:**
> Well, maybe I'm having a more thorough problem. I'll manage using this solution, but I think I'll just reinstall when 11.04 comes out, solving all problems.

If anybody has a different solution, please reply so I can try it out.


Seriously, did you guys see titoaii's reply? It's the actual solution and you get back the sound and message indicators. It worked for me, thanks titoaii.

---

### Post by Nicondrio on 2010-10-20
Like I said before, it didn't work for me unfortunately so maybe there is a different problem going on. It's nice that it worked for you.

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-10-20
Right click on the top panel and select add to panel then add "Indicator applet". I think that should work. tell me if it does. That's how I do it because I customize the top panel a lot

---

### Post by Nicondrio on 2010-10-20
Hmm, it doesn't make any sense, but somehow it came back. I tried adding the indicator applet again, this time with succes. Maybe the updates I loaded this morning helped to do the trick.

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-10-20
The only problem I have with this applet is that when I get a new message in evolution the envelope doesn't become green. if anyone knows how to fix it I'd made a thread about it a couple of days ago.

---

### Post by Arminho on 2010-11-21
> **nicholasbgr said:**
> Seriously, did you guys see titoaii's reply? It's the actual solution and you get back the sound and message indicators. It worked for me, thanks titoaii.

titoaii's solution worked for me, too. Thx titoaii!

I experienced some problems to find the right entry to add. For it worked to enter "indicator" in the top right text input field on the "Add to panel" menu.

---

### Post by angel_gb on 2010-12-30
(Sorry for my English)

I Accidentally removed the new [[COLOR="Blue"]SoundMenu[/COLOR]]("https://launchpad.net/indicator-sound") from main panel.

You have proposed two solutions in this thread:

- Install the classic ***gnome-volume-control-applet***, but I wanted de new one.

- Add the ***Indicator applet*** again to the bar. In my case this didn't work, email button appeared but volume button is still missed.

I manage to restore the new [[COLOR="blue"]SoundMenu[/COLOR]]("https://wiki.ubuntu.com/SoundMenu") by installing ***indicator-sound*** packet.

I hope to be useful.

---

### Post by Lamellama on 2011-01-04
> **titoaii said:**
> Hi!

I had the same problem. It seems difficult to resolve but it isn't.
Just right click over the panel. select add to panel and add the  (i don't know the exact name in English but in Spanish is Miniaplicación de indicadores) Mini-applet of indicators or something similar.

I hope this could help.

Regards!

Thank you, the indicator thing should be labelled more clearly.

---

