---
title: "my kde looks odd"
date: 2009-11-30
forum: Desktop Environments
---

### Post by hirohitosan on 2009-11-30
hi there. I have Ubuntu on my laptop and I installed also kubuntu-desktop. After install my KDE looks very odd. I don't know if it is because my hardware or is something else.Gnome works perfectly.
As you can see in the "snapshot2" the bottom panel is invisible and windows decoration are invisible too.

any help?

thanks

---

### Post by lykwydchykyn on 2009-11-30
Looks like it doesn't like your graphics driver.  Try hitting alt-shift-f12 to turn off compositing and see if that makes a difference.

---

### Post by hirohitosan on 2009-11-30
> **lykwydchykyn said:**
> Looks like it doesn't like your graphics driver.  Try hitting alt-shift-f12 to turn off compositing and see if that makes a difference.

nothing happened with alt-shift-f12

so what can I do in this case?

and I have no Internet in kde. Do I need to enable separately in KDE? How?

thanks

---

### Post by lykwydchykyn on 2009-11-30
KDE uses its own front-end to network manager, but beyond that it's the same as Ubuntu as far as I know.  

Let's fix one problem at a time, though.

Open system settings, go to "Look & feel"=>"Appearance"=>"Desktop"=>"Desktop effects" and uncheck "Enable desktop effects" to see if your visuals are fixed.


What sort of computer/video hardware are you running this on?

---

### Post by hirohitosan on 2009-11-30
> **lykwydchykyn said:**
> Open system settings, go to "Look & feel"=>"Appearance"=>"Desktop"=>"Desktop effects" and uncheck "Enable desktop effects" to see if your visuals are fixed.
I cannot see any buttons or menu. I Alt+F2 > konqueror > settings:/ and desktop effects are not enabled 

> **lykwydchykyn said:**
> What sort of computer/video hardware are you running this on?


VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]

---

### Post by lykwydchykyn on 2009-11-30
> **hirohitosan said:**
> I cannot see any buttons or menu. I'm trying to find a way to start system settings with konsole

Hit alt-f2 and type "system settings".  That should bring it up.  Or, better yet, type "desktop effects" to go straight to the relevant module.
> 
I have ATI Radeon 9600

Hrm... I'm not very experienced with ATI, other than my wife's laptop which I can't get decent compositing on for the life of me.  Maybe an ATI guru will show up to help.

---

### Post by benerivo on 2009-11-30
Open the settings with```
systemsettings
```either from a console or by pressing the Alt+F2 to bring up krunner.

---

