---
title: "Hibernate Button"
date: 2005-10-13
forum: Desktop Environments
---

### Post by thieummm on 2005-10-13
Does anyone know where the Hibernate/Suspend button is hiding in KDE ?
Is there any ?

---

### Post by daller on 2005-10-13
Running on a laptop???

- then you need to use the "klaptopdaemon" (K-menu -> System Settings -> Laptops & Power (under hardware) -> Laptop-battery -> Start battery monitor)

If its a desktop machine, I have no answer for you! (I'm looking for at solution myself!)

---

### Post by mlord on 2005-10-13
Once enabled (see daller's posting), the hibernate and suspend "buttons" are available on the Right-Click menu of the power (plg/battery) icon (near lower right corner of the taskbar)

---

### Post by wrtrdood on 2005-10-20
Well... almost.

Once you get KLaptop started then you'll need to configure it.  There's tabs at the top and you have to enable the "helper apps" on the last tab (labled ACPI, I think).  Then standby and suspend show up under the other tabs.  Hibernate is there by default, I believe.

As long as your system is ACPI compliant, you should be able to use KLaptop to control the power profiles even on a desktop.  Obviously the "battery" selections would be of little value but I'd think that the rest would work just fine.

A note to those using 3.5Beta --- this thing works like a charm, at least for me.  After configuring things (as mentioned above) I now have a fully functional power management profile for my laptop.  It simply "just works".  Hats off to the developers.  Closing the lid immediately sends my laptop to sleep and opening it brings me right back to where I was.  No ALT-F7 fumbling at all.  It's been a long wait for such a simple thing.  Even the timeout works.  I'm a happy camper.  The only issue I have now is a long-standing one: the trackpoint doesn't recover.  Simple function key operation to re-enable so no biggie.  It's a psmouse thing...

---

### Post by thieummm on 2005-10-21
Thanx for the answers.

Why is the Hibernate facility hidden in Klaptop  ?
Wouldn't that be better to integrate it in the logoff screen ?

---

### Post by tux73 on 2005-10-29
You can configure Klaptop to go into "sleep" whenever you close the laptop-lit.

But of course, I asked the same question to me first. An additional logoff-option "suspend" would be great - but this is inside KDM and must be integrated there.

---

### Post by coaxx on 2005-12-29
[QUOTE=tux73]You can configure Klaptop to go into "sleep" whenever you close the laptop-lit.

But of course, I asked the same question to me first. An additional logoff-option "suspend" would be great - but this is inside KDM and must be integrated there.[/QUOTE]

I agree with You this shouldt really be integrated in KDE "Startmenue". But till then one can add a Applicationbutton to the panel, so You are just a click away from going to sleep. Just use the same properties as used for the "Adept" Starter in KDE Menue and usw "etc/acpi/sleep.sh" for the command! If You like You can also change thje icon.

---

