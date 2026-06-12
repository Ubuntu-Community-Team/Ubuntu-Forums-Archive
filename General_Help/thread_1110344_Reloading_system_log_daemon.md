---
title: "Reloading system log daemon"
date: 2009-03-29
forum: General Help
---

### Post by Steinar on 2009-03-29
Xubuntu 8.10

I'm running fvwm2, surfing the web with Opera, and am using my touchpad when the machine suddenly switches to text-mode (as when you press ctrl-alt-f1) and says:

[FONT="Courier New"]* Reloading system log daemon ...
  ...done.[/FONT]

After a few moments, I am taken back to the login screen and all my work was lost.

The terminal (ctrl-alt-f7) is still available with the text above.

Any insight on what may be causing this?  Is it likely to happen again?

---

### Post by dcstar on 2009-03-30
> **Steinar said:**
> Xubuntu 8.10

I'm running fvwm2, surfing the web with Opera, and am using my touchpad when the machine suddenly switches to text-mode (as when you press ctrl-alt-f1) and says:

[FONT="Courier New"]* Reloading system log daemon ...
  ...done.[/FONT]

After a few moments, I am taken back to the login screen and all my work was lost.

The terminal (ctrl-alt-f7) is still available with the text above.

Any insight on what may be causing this?  Is it likely to happen again?

The text is just the remains of the startup sequence and has nothing whatsoever to do with your problem - which seems to be the X server crashing and restarting.

---

