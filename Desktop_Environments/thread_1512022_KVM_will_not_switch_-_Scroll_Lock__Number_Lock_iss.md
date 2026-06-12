---
title: "KVM will not switch - Scroll Lock / Number Lock issues"
date: 2010-06-17
forum: Desktop Environments
---

### Post by Jaytech on 2010-06-17
Greetings,

I have a Rosewill RKV-2U USB KVM switch attached to a Kubuntu 10.04 64-bit system. Keyboard attached is a MS Comfort Curve 2000 USB and the mouse is a Logitech MX510. 

My problem is that the KVM will not respond to switching hotkeys (Scroll Lock or Num Lock) when controlling the KDE desktop environment under Ubuntu (KDM). Oddly enough, the hotkeys work great when the desktop is changed to Gnome (GDM). 

I worked through all the potential solutions discussed in [this older thread]("http://ubuntuforums.org/showthread.php?t=231700"), but I did not find one that worked.

Switching (for both keys) works when I drop to the terminal (Alt-Ctrl-F1). However, once I'm back in the KDM the hotkeys stop working; the keys themselves function as normal, just not for switching the KVM. As a side note, my scroll lock led turns off and will not function again until I leave the KDM session.

The KVM hotkeys seem to function well with other operating systems Centos/KDE, WinXP, WinVista, Win7, and various Linux Live-CDs.

I would appreciate *any* thoughts or input on this issue; it's driving me nuts! Thanks!

---

### Post by Jaytech on 2010-06-18
No ideas? Anyone?

---

### Post by tamuchin on 2010-10-29
I have had this problem and have searched over and over.  The best solution I found is to create your own keymapping in kde using System Settings -> Input Actions and then go to the bottom left where it says "Edit" and select New -> Global Shortcut -> Command/URL.

Then under "Action" for Command/URL put this:

xset led named "Scroll Lock";sleep 1;xset -led named "Scroll Lock"

Under "Trigger" select a key sequence you would like to use (I used Ctrl+Scroll Lock) and hit Apply and you should be ready to go.  The command turns the scroll lock light on, waits a second and then turns it off again.  I guess the kvm switch actually looks for the light.

This solution worked for me hope it works for you.

There is also the never failing but more cumbersome use Ctrl+Alt+F1 and then hit scroll lock (or num lock) twice and then when you return back hit Ctrl+Alt+F7 to get back to the x session.  I don't like that one though.

---

### Post by Drezliok on 2011-12-30
I have the same problem but I can't seem to apply the fix. I am using Unity on one pc and Lubuntu on another Pc.

---

