---
title: "fglrx driver and small font sizes"
date: 2006-10-11
forum: Desktop Environments
---

### Post by dcherryholmes on 2006-10-11
After installing the fglrx driver all of my fonts are much smaller.  Has anyone else seen this?  I checked in the Font GUI under "Details" and the DPI is still set to 96 DPI.  Anything else I can check?

---

### Post by dcherryholmes on 2006-10-12
A little more info:

xdpyinfo yields the following:

screen #0:
  dimensions:    1024x768 pixels (400x300 millimeters)
  resolution:    65x65 dots per inch
  depths (7):    24, 1, 4, 8, 15, 16, 32

So, if I'm reading this correctly it means I'm actually running at 65 DPI, not 96?  Could this be the cause of the uber-tiny fonts I have now?  Any ideas how to fix this?  I tried creating /etc/fonts/local.conf with the following:

<match target="pattern">
        <edit name="dpi" mode="assign"><double>96</double></edit>
     </match>

.... but it didn't seem to help.

---

### Post by dcherryholmes on 2006-10-31
It wasn't the fglrx driver.  It was Xgl.  Adding gnome-session-manager to my startup programs (System -> Preferences -> Sessions -> Startup Programs) fixed it.

---

### Post by MikeEx on 2006-11-19
I am having this issue as well but neither of those things helped.

](*,) 

Can some one please shed some light on this?

---

