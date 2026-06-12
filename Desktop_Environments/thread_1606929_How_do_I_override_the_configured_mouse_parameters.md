---
title: "How do I override the configured mouse parameters?"
date: 2010-10-27
forum: Desktop Environments
---

### Post by Paul Elliott on 2010-10-27
How do I override the configured mouse parameters? I want to declare two of my trackball's buttons to be draglocks. I have created and edited a /etc/X11/xorg.conf. But it seems the configured mouse is overriding what I put in xorg.conf.

If I add

Section "ServerFlags"
        Option "AutoAddDevices" "false" 
EndSectionThen my keyboard stops working.

How can I override the configured mouse options to specify drag lock buttons?

Thank You.

---

### Post by Paul Elliott on 2010-10-27
solution

add the line
xinput --set-int-prop 'ImExPS/2 Generic Explorer Mouse' 'Evdev Drag Lock Buttons' 8 8 1 9 3

to .xprofile added my DragLock buttons. Not the first 8 above is the property format. "8 1 9 3" are the drag lock buttons. You could do it globally with /etc/X11/xinit/xinitrc.

I never did figure how to do it with /etc/X11/xorg.conf

---

