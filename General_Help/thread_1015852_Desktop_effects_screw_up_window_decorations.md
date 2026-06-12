---
title: "Desktop effects screw up window decorations"
date: 2008-12-19
forum: General Help
---

### Post by tbraun on 2008-12-19
Even when I enable only mild desktop effects ("Normal" in the "Visual Effects" tab in 8.10 with Gnome 2.24.1), the window decorations often (but not always) get screwed up. Please see the attached screenshot to see what I mean. Take a look at the title bar and the maximize and close buttons. I tried different themes, but it's always the same.

The effect usually happens when you click in and out of a window a couple of times, but often also appears when the window is opened for the first time.

Any idea what's causing this and how to fix it?

This happens on a Dell Latitude D820 laptop. 'lspci' tells me the following about my graphic card and driver:

[INDENT][FONT="Courier New"]01:00.0 VGA compatible controller: nVidia Corporation G72M [GeForce Go 7400] (rev a1)[/FONT][/INDENT]

I also installed the Compiz settings manager, but couldn't find anything (obvious?) that would apply to this situation.

Thank you very much in advance for any help.

---

### Post by eternalnewbee on 2008-12-19
What's your distro?
Could be a driver issue

---

### Post by FuturePilot on 2008-12-19
This is a known bug with the Nvidia driver. I believe it was fixed in the 180 driver, but it's still in Beta at the moment.

---

