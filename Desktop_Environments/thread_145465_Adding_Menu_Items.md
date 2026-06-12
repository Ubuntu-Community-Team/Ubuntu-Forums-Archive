---
title: "Adding Menu Items"
date: 2006-03-16
forum: Desktop Environments
---

### Post by c_williams on 2006-03-16
I have been adding some menu items using smeg and I am having some issues with some that run in a terminal window.  For instance, if I create a menu item to run the command "/bin/ps aux" and I check the "Run In Terminal", when I try to launch that menu item, the terminal window pops up and then quickly closes.  How do I make it so that the window will stay open?

Thanks for the assistance.

---

### Post by timetunnel on 2006-03-16
I think you must write a shell script for that and make it wait for user input. It would look like this:
```
#!/bin/bash
/bin/ps aux
echo Press RETURN to exit
read text

```
You can then point your menu item to that script.

Jens

---

