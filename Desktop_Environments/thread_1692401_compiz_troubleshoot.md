---
title: "compiz troubleshoot"
date: 2011-02-21
forum: Desktop Environments
---

### Post by Einstein86 on 2011-02-21
[INDENT]This is problem of mine: I have turned on 'brightness, saturation and transparency' in compizconfig  and cause that only can see desktop with shortcuts on it but nothing else. If I run any application or open window it does that but i cannot have a look of its like i'm blind. I know it's transparent 100%, but dunno what to do? Actually dunno how to restore because can't see where to click with mouse.
[/INDENT][INDENT]Please for help through concrete steps.
[/INDENT]

---

### Post by Forlong on 2011-02-21
Boot into the failsafe GNOME session from GDM (login manager). It should boot GNOME without Compiz being enabled, so you can fix it.

---

### Post by Krytarik on 2011-02-23
For anyone setting up those rules: The "New" dialogs for lists in Compiz don't offer a "Close" option, and even closing the window with the "X" button sets the new rule. So, if you want to cancel the creation of the rule, just enter something unreal, like "dgdfgd" ;-), otherwise your desktop can quickly go bust.

I had that just yesterday with the "Size" option in the "Window Rules" plugin, I guess it was filling up my swap space while trying to set all windows to negative size values (I wonder how that makes sense.). I had to use the recovery mode, because I have autologin enabled.

Also, don't confirm the "Add" dialogs, it doesn't set the value you may have entered or "grabbed" before, just the "class=" or whatever is selected with no value, resulting in ALL.

Greetings.

---

### Post by Einstein86 on 2011-02-27
thanks guys

---

### Post by stinkeye on 2011-02-27
...and for others who run into this problem 
you can use alt+mousewheel up/down to alter transparency when the mouse is 
hovered over the window.

---

### Post by Krytarik on 2011-02-27
> **stinkeye said:**
> ...and for others who run into this problem 
you can use alt+mousewheel up/down to alter transparency when the mouse is 
hovered over the window.
When I had those transparency issue, I could simply press Alt+F2 and enter "metacity --replace" blindly ;-), but that wasn't even possible in my described case.

---

