---
title: "Right click menu shadows disappeared on desktop &amp; Nautilus"
date: 2010-07-03
forum: Desktop Environments
---

### Post by SirPecanGum on 2010-07-03
Ubuntu 10.04 - Right click menu shadows have disappeared on desktop & in Nautilus but are still present on the panel, main menus and other apps. Changing theme and turning on / off desktop effects make no difference. Any ideas?

---

### Post by Japa on 2010-09-04
In Compiz settings open window decoration and replace text under shadow windows from "any" to "any (class=Tooltip | Menu | PopupMenu | DropdownMenu | Unknown)". I got this info from following thread [http://wwww.ubuntuforums.org/showthread.php?t=1521911](http://wwww.ubuntuforums.org/showthread.php?t=1521911)

---

### Post by rohu2187 on 2011-04-17
hey japa ....
Thanks man... that was really helpful.

---

### Post by johnconnor on 2011-05-16
Hello!

That trick did not work for me.  Still no shadows under desktop and Nautilus right-click menus for me :(

Anyone else experiencing this peculiar issue?

FYI, I’m running Natty.

---

### Post by quantruong1985 on 2011-08-02
If you are using Nautilus Elementary, there's no shadow when right click on desktop or in Nautilus because of the conflict with Compiz. Do these steps to solve it:
- In Nautilus : select menu Edit->Preferences->Tweaks -> under Application uncheck "Enable rgba transparency".
- In CCSM : Enable Windows Decoration, at Windows shadow line, replace "any" with "any (class=Tooltip | Menu | PopupMenu | DropdownMenu | Unknown)" (without quotes).
- If there's still no shadow, restart Nautilus by typing this line in Terminal : "nautilus -q" (without quotes).:popcorn:

---

### Post by johnconnor on 2011-08-02
Disabling rgba transparency did the trick! :p

---

### Post by quantruong1985 on 2011-08-03
> **johnconnor said:**
> Disabling rgba transparency did the trick! :p

Cheers!

---

