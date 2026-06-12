---
title: "running solaris application on gnome display"
date: 2011-05-24
forum: Desktop Environments
---

### Post by tonycnb on 2011-05-24
Hi all - I'm running ubuntu 10.10 (with the macbunu theme if it matters).  From there, I'm running an application on a solaris system and forwarding the X11 display back to my ubuntu/gnome display with the follow command "ssh -X <solaris-host>".  

Everything seems to display correctly so far except for what I would describe as the alert boxes.  The problem is they are invisible.  I know it's there because I have mouse pointer jumping turned on and the mouse jumps to the default button and if I click on it the alert box flashes and but disappears.  The disappearing is normal due to the button press.  So it appears the alert box is present but invisible until I click a button but disappears immediately because of the button press.  

Any help would be greatly appreciated,
Tony

---

### Post by tonycnb on 2011-05-25
This is a follow up to my post.  Further research has revealed to me that GNOME is not the window manager rather it is a desktop.  So it would appear that the problem I'm having is due to a limitation of some kind in Compiz.  I guess I was a bit confused since I installed OLWM and selected it instead of GNOME at login time.  The alert box works properly in OLWM.  If I can just get the macbuntu theme to work with OLWM I'd be happy but so far I think that would be hopeful.  So I'm currently I'm digging around for Compiz options that would allow the alert boxes to display.

Tony

---

### Post by tonycnb on 2011-06-17
Some three weeks later I'm still at it.  I have a system that I was able to reload ubuntu 10.10 on and with a fresh load the system is able to display the invisible popup alert boxes.  This only works if I set "System -> Preferences -> Appearance -> Visual Effects" to None.  If I set it to Normal or Extra the popup become invisible again.  

So my new question is: can anyone tell me what the "System -> Preferences -> Appearance -> Visual Effects" affects in the system or at least tell me where I can look in the system so I can try to isolate what is happening.

Anyone with me or am I alone with this one?

Any help would very much appreciated.
Tony

---

