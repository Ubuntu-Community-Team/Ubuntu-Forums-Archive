---
title: "Disable workspace swich with mousewheel"
date: 2007-12-05
forum: Desktop Environments
---

### Post by musther on 2007-12-05
When using my laptop I often get annoyed that my workspace changes if my finger strays into the zone of the touchpad designated for mouse wheel behaviour.  Of course, this only happens when the mouse pointer is over the desktop background, but it can still be rather annoying.  Does anybody know of any way to disable this behaviour?

Thanks.

---

### Post by ryanrich on 2007-12-05
I'm also looking for a solution to this, it's FREAKIN' annoying! :lolflag:

---

### Post by musther on 2007-12-05
Oh, never mind, I finally tracked it down in the compiz plugins, wasn't where I expected though.  

If anyone wants to know, you'll need to have compizconfig-settings-manager installed, then open the Advanced Desktop Effects Settings from the preferences menu, and find viewport switcher, then look at the Bindings section.

---

### Post by weezalxc on 2007-12-05
I dont see a Bindings section in the Viewport Switcher options.  All I see are Desktop-Based Viewport Switching and Actions.  I looked in Actions - but I dont see anything about the scroll wheel.

---

### Post by CarpKing on 2007-12-05
> **weezalxc said:**
> I dont see a Bindings section in the Viewport Switcher options.  All I see are Desktop-Based Viewport Switching and Actions.  I looked in Actions - but I dont see anything about the scroll wheel.

It will be listed as "mouse button 3" or somesuch.

---

### Post by weezalxc on 2007-12-05
Thanks!  I had to replace Button4 and Button5 with none :)

---

### Post by z-bot on 2008-01-26
Worked like a charm.  Thanks!

---

### Post by metalf8801 on 2008-02-15
> **musther said:**
> Oh, never mind, I finally tracked it down in the compiz plugins, wasn't where I expected though.  

If anyone wants to know, you'll need to have compizconfig-settings-manager installed, then open the Advanced Desktop Effects Settings from the preferences menu, and find viewport switcher, then look at the Bindings section.

Thanks that helped me a lot

---

### Post by sgornick on 2008-04-26
For the beginner, here are the steps to disable the ability for the scroll wheel to change workspace in Compiz.

If you don't already have compizconfig-settings-manager installed,
  $ sudo apt-get install compizconfig-settings-manager

Then 
  System -> 
    Preferences ->
      Advanced Desktop Effects Settings

  Select the Desktop category.
  Click on the Viewport Switcher icon
  Click on the Edit icon next to Button5 (Move Next entry),
   and change the value to "None".
  Click on the Edit icon next to Button4 (Move Prev entry),
   and change the value to "None".

Scroll wheel will no longer do a "Move Next" or "Move Prev".

---

