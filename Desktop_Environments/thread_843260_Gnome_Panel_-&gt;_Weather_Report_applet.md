---
title: "Gnome Panel -&gt; Weather Report applet"
date: 2008-06-28
forum: Desktop Environments
---

### Post by Okar on 2008-06-28
Hi,
is there any method to invoke the update function of a Weather Report applet in the Gnome Panel.
The problem I got is that I want it to update as soon as my internet connection is established.
As the applet probably tries to update right after the startup when the connection is not established yet, therefor I have to manually update or wait XY minutes. 
I got a dispatcher script for the Network Manager anyway.
ty

---

### Post by mcduck on 2008-06-28
If I remember right the update should be an option in that applet's right-click menu..

---

### Post by Okar on 2008-06-28
yes that's true, but I want to invoke this behavior from a script.

---

### Post by TorqueyPete on 2008-06-28
Cool! I didn't know that Gnome had that! I'll have a look for it now. :)
 In spite of the fact that I sit in front of my PC a lot, I also go outside a lot! Kite flying and stuff. ;) 
If you're in the UK, try the Met Office's own [_free weather gadget_]("http://www.metoffice.gov.uk/weather/uk/gadgets/firefox.html"). I think it updates every few hours.
 Heres a screenshot.
 The gadget button is visible in the lower rh corner.

[IMG]http://i81.photobucket.com/albums/j226/chashugh/Screenshot.png[/IMG]

---

### Post by phxrider on 2009-02-23
killall gnome-panel

...will cause it to update, but it also kills the panels for a second or 2 until they restart.

---

