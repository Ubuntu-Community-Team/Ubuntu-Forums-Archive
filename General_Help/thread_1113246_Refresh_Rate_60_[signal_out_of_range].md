---
title: "Refresh Rate 60 [signal out of range]"
date: 2009-04-01
forum: General Help
---

### Post by tempp on 2009-04-01
Okey i installed xubuntu yesterday on my old machine.
Had to drag in another monitor sense the default refresh rate was to high and i had to set it to 60.

after changing i plugged in my monitor and it works but each time i start the pc i dont get eny picture just signal out of range.
I have to drag in another monitor restart pc and after 
seeing the login screen i can swap in my lcd and get a working picture.

Is there anyway to fix it?

---

### Post by SubNetMask on 2009-04-01
> **tempp said:**
> Okey i installed xubuntu yesterday on my old machine.
Had to drag in another monitor sense the default refresh rate was to high and i had to set it to 60.

after changing i plugged in my monitor and it works but each time i start the pc i dont get eny picture just signal out of range.
I have to drag in another monitor restart pc and after 
seeing the login screen i can swap in my lcd and get a working picture.
i
Is there anyway to fix it?

Yes, i had this same problem, run it LIVE in safe graphics mode, (Press F4, pick safe graphics) then once you get it booted up, open:

     System > Administration > hardware drivers

Enable the proprietary driver, LOG OFF, don't shut off, and log back on, just press enter, don't enter in any names, and install.

Hope that fixes it.

---

