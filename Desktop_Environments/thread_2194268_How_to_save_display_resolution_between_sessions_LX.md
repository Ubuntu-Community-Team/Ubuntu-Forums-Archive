---
title: "How to save display resolution between sessions LXDE"
date: 2013-12-17
forum: Desktop Environments
---

### Post by pha3r0 on 2013-12-17
Hi folks I want to take a minute and explain what I just did to SOLVE the problem people are having with display resolution settings not being persistent from session to session. I hope this will save some people some headaches, since i just spent 4 hours trying different approaches to varying degrees of success and then stumbled on what seems is the **easy way...**

First to clarify im using Lubuntu 13.10 and simply put, the 'issue' is that at every login/reboot you have to use lxrandr (or xrandr) to set the display resolution (for me it was from 1024x768 to 1280x1024) 

Here is the step by step starting from login:
[HR][/HR]
**1.** Open the menu and select Preferences>Monitor Settings (lxrandr).
**2.** Select your desired default resolution and click 'Save', you can repeat and use 'Apply' at this point if you need more screen size for the rest of this...
**3.** Press alt+f2 and input **'leafpad ~/.config/autostart/lxrandr-autostart.desktop'**. In the file that opens you will see a line begining with 'Exec=xrandr ...' highlight and copy(ctrl+c) everything after the = sign then close leafpad
**4.** Again open the menu this time go to Preferences>Default applications for LXsession (lxsession-default-apps)
**5.** On the left side go to the fourth tab (Options) and there you will see the fourth entry down is XRandr.
**6.** Change the 'mode' to 'command' and in the 'command' box paste(ctrl+v) what we just copied from leafpad. It should start with 'xrandr --output ...'
**7.** Click Apply and Reload (if you didn't repeat step 2 this will activate your desired resolution setting)
[HR][/HR]
**THATS IT!!!** you should now have whatever setting you chose activate each time you log in. You don't need to edit any other files or even learn all of the options of **xrandr**. However you are not limited to just this command you can put whatever xrandr command you want in the XRandr entry in lxsession-default-apps. For instance setup multiple monitors, use panning and virtual desktop sizes, anything xrandr will allow, see [B]man xrandr
[/B] or **xrandr --help**

It would be nice to have this info marked for the Lubuntu croud or even edited into a nice HOW-TO (you have my permission). Whatever the admin's care to do with it. Also if some guru has some free time im sure this can all be done in 3 or 4 lines on a terminal...

Thanks for reading and I hope this helps

---

### Post by robbie 348 on 2013-12-19
Thanks for the tip, it worked perfect, Rob.

---

### Post by websterthehamster2 on 2014-01-12
I found my **lxrandr-autostart.desktop **&#8203;file to be completely empty for some reason. Any ideas?

---

### Post by ptrwcz on 2014-01-20
I have same issue: **lxrandr-autostart.desktop &#8203;file - completely empty**

---

### Post by primaeval on 2014-01-21
> **ptrwcz said:**
> I have same issue: **lxrandr-autostart.desktop &#8203;file - completely empty**

Try launching an editor from a terminal. I had the same problem.

---

