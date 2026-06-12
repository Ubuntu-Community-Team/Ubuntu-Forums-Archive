---
title: "Strange title bar problem"
date: 2007-11-07
forum: Desktop Environments
---

### Post by gb5uqx on 2007-11-07
Installing scheduled updates on Gutsy yesterday wiped all my display and desktop setting for some reason. However I have now got things back to normal except the window maximize, minimize and close buttons are gone. This is not the usual problem where the whole title bar goes. This time the title bar is there but all the buttons are gone.

The applications icons sit in the middle of the title bar when they usually sit extreme left. This is only occurring with no desktop effects enabled, my preferred option. Enabling desktop effects makes everything as normal but not as required nor as they once were.

Any ideas?

---

### Post by gb5uqx on 2007-11-07
Go to “Applications -> System Tools -> Configuration Editor

Go to /apps/metacity/general/

Go to the **button_layout** key and make sure it reads **menu:minimize,maximize,close**

Original settings had been lost in update, key setting was now <no value>

Can also be accessed from terminal using **gconf-editor**

---

