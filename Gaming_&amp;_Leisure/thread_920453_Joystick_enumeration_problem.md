---
title: "Joystick enumeration problem"
date: 2008-09-15
forum: Gaming &amp; Leisure
---

### Post by Neil_J on 2008-09-15
I've been trying to setup X-Plane flight sim to work with two input devices, a Saitek ST290 USB joystick, and a set of CH Products Pro rudder pedals (also USB).  From a cold boot, if I plug in either of these, I get TWO devices in /dev/input: js0 and js1.  

js0 gets enumerated as 'Microsoft USB Keyboard' -- This should not be here.
js1 gets correctly enumerated as 'Saitek ST290 joystick'.

If I plug in my rudder pedals at this point, it comes up as js2.

Something is obviously wrong here, why does my keyboard get enumerated as a joystick?  More importantly, why does is only come up when I plug in my ST290 joystick?  The bad part about this is, the 'keyboard joystick' apparently has 50-100 buttons, which grab all of the available buttons in X-Plane.  

If I try this on a different machine with Ubuntu 8.04, I get the same thing.  It doesn't matter if I plug the rudder pedals or the ST290 in first.  One interesting thing, it doesn't happen on my Asus Eee notebook running Ubuntu 8.04 -- but it doesn't have a Microsoft keyboard, so maybe there's a conflict between certain keyboards and joysticks?

Right now the only way I can play X-Plane is on a Mac or Windows box... I would much rather get it working on Ubuntu however.  Has anyone seen this behavior before, and if so, is there anything I can do about it?

---

### Post by Neil_J on 2008-09-21
bump, I'm still not able to use my joystick(s)... Can anyone help?

---

### Post by bilbrey on 2008-10-17
Contributing bump - this happens to me, too. Plug in the 'stick (in this case a Logitech Extreme 3D Pro), the "MS Wireless Optical Desktop" enumerates as js0, brings the joystick in at js1, and pushes most of the axes and all of the buttons off the end of the X-Plane joystick configuration.  I'll keep looking ...

.brian

---

