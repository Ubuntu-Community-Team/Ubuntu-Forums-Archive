---
title: "Different question on ButtonMapping and multiple pointers"
date: 2007-02-19
forum: Desktop Environments
---

### Post by shotgunefx on 2007-02-19
I'm having a problem with ButtonMapping that I hope someone can shed some light on.

I currently have three input devices, a PS/2 mouse (Mouse0 Corepointer), a USB mouse (usbmouse) and a touchscreen (touchscreen).

Mouse0 has 3 physical buttons, what I'd like to do is map these higher (say 7,8,9) while leaving usbmouse unaffected. No matter what I try, this won't work.

Using xmodmap, changes both mice. Using xinput doesn't appear to do anything. 

If I do an **xinput list**, I see Mouse0, but if I try something like 
**xinput set-button-map Mouse0 4 5 6 1 2 3**, 

I get an error **Unable to find device "Mouse0"**

If I try and use ButtonMapping in xorg.conf, it will use the same ButtonMapping for both mice, even though they both have separate ButtonMappings.

If you are wondering why someone would want to do such a thing, this is for my carpc, and Mouse0 is a mouse I fabbed into my shifter. 

[IMG]http://lib.store.yahoo.net/lib/leeland/dshift-installed.jpg[/IMG]

I want to use the buttons on the shifter for application specific behavior, so when I'm in my music player, I can scroll through the playlist, or toggle through the front and rear cameras, etc. 

I'm running xorg 7.1.1, any help would be greatly appreciated.

Thanks,
-Lee

---

### Post by shotgunefx on 2007-02-21
:confused:

---

