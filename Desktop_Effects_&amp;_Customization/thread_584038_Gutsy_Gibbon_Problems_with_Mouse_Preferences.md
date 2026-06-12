---
title: "Gutsy Gibbon: Problems with Mouse Preferences"
date: 2007-10-20
forum: Desktop Effects &amp; Customization
---

### Post by vmoros on 2007-10-20
Hi guys,

I installed Gutsy Gibbon on my Dell Latitude D630 Laptop and everything worked great. As I was customizing it to look how I wanted it to and act like I wanted it to, I went to the mouse preferences. I Noticed that there was no pointers tab so I could not change my mouse pointer nor could I tell it to show my cursor when I press Ctrl, but in the help file it talks about the pointers tab. Does anyone know how I could change the settings normally accessed in the pointers tab?

---

### Post by FuturePilot on 2007-10-20
The Pointers tab has been moved to a new home:lolflag:
You can find it by going System>Preferences>Appearance. Click on the Customize button and the very last tab is "Pointer"

---

### Post by vmoros on 2007-10-20
Thanks FuturePilot.
But I noticed that in the Pointers tab in the Customize options that there is no option to locate the mouse when I press Ctrl. So is this option totally gone?

---

### Post by Nuno Bettencourt on 2007-10-25
Hi, 

I'm also interested in this feature, for opposite reasons :)

I used ctrl to show my current cursor position and now I want to disable it (I had it enabled before upgrading to gutsy). Nevertheless, the pointers tab is gone and, since I'm not an experience user, I don't know how to do it without that tab. 

Cheers

--------

After some digging, i found out that you can use gconf-editor to change the "Locate Pointer" show option. Just run it through a terminal console and locate a key with name /desktop/gnome/peripherals/mouse/locate_pointer. Afterwards check it or not according to your will.

---

