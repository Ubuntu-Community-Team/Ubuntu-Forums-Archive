---
title: "Dapper gdm doesn't redraw background image"
date: 2007-01-13
forum: Desktop Environments
---

### Post by dwtokarski on 2007-01-13
Here's an odd one...  On several of the Dapper installs I've deployed over the last few months, gdm does not redraw the background login screen splash image after the system has been left untouched for several hours.

After that length of time, the screen is blank of course, with the monitor on standby. Move the mouse and the monitor comes on, followed in a few seconds by the login screen.  The text box for entering the login id is there and works, the options menu in the lower left corner is there and works, but the background image is replaced by alternating white and grey lines--fairly thin ones, about four or five scan lines thick.

Interestingly, if the options menu is actually opened, the background image *is* redrawn. Switching to a text console and back also forces an image redraw.  It's almost like gdm is waiting for an event to provoke the screen redraw, but a simple monitor wakeup isn't doing that.

I don't have an inventory of all the hardware combinations which display this behavior, but the two boxes close at hand which do are older K6 systems using a couple of variations on the Asus TX97 motherboard with 256 MB, and Trident PCI video cards which identify as "TGUI 9660" (xorg driver is "trident").

Anybody out there got a clue for me?

---

### Post by dwtokarski on 2007-01-24
> 9660" (xorg driver is "trident").

Anybody out there got a clue for me?

OK, I take the silence as a "no".  Here's an observation from my continued fiddling with this problem which might help.

On the two nearly identical systems I have set up with Trident TGUI 9660 cards, one behaves as described in my opening post. Behavior of the second is now slightly different--the background image when the screen comes on is as usual replaced by alternating light and dark horizontal lines, but now moving the mouse leaves a trail of restored background image in its wake.  The mouse cursor moves a square area about a 1cm on a side, kind of like using a large square brush in GIMP.  Screen area over which this "brush" is drawn has the login screen background image restored, while leaving the rest of the screen untouched.

The device section of xorg.conf for the second system was changed to look like this:

```

Section "Device"
        Identifier      "Trident Microsystems TGUI 9660/938x/968x"
        Driver          "trident"
        BusID           "PCI:0:11:0"
        Option          "ShadowFB"      "true"
EndSection

```

Adding the ShadowFB option to second system changed the behavior as described. It's also a lot slower.

Does that shake loose any ideas?

---

