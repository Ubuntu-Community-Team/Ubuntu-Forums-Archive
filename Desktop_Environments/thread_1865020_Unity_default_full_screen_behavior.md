---
title: "Unity default full screen behavior"
date: 2011-10-19
forum: Desktop Environments
---

### Post by msrk on 2011-10-19
Every time I open an application, say my web browser or pdf viewer, it opens full screen.  I tried reducing the window size and closing the applications hoping Unity would save my preference.  It did not.  Is there a way to set the default behavior of Unity so that it does not open any applications in full-screen mode?

Thank you.

---

### Post by JRV on 2011-10-19
Yes, open a terminal and enter this code:
```

sudo apt-get install compizconfig-settings-manager
ccsm

```

Near the bottom of the page, uncheck "Grid"

Then open the Ubuntu Unity Plugin under the Desktop heading.

Click on "Experimental" and change the "Automaximize Value" to 100%.

---

### Post by stair314 on 2011-11-05
My "Experimental" tab does not have the "Automaximize value" available. Is this only available in 11.10? Is there any other way to turn off automaximization in 11.04?

---

