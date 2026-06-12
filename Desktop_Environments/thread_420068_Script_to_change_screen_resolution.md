---
title: "Script to change screen resolution"
date: 2007-04-23
forum: Desktop Environments
---

### Post by n8wood on 2007-04-23
How do I change the resolution in X through the command line?

I would like to create a script that I can run when I undock my laptop so it displays the proper resolution on the laptop screen. I can do this manually with the "Screen Resolution" utility, but a script would be more efficient. 

thanks.

---

### Post by heimo on 2007-04-23
xrandr can do that. Run without flags to get list of available sizes. Then use it with -s to select one of those modes. (eg: xranrd -s 1)

---

### Post by n8wood on 2007-04-23
Awesome! It works and will do exactly what I need!

---

### Post by ssd008 on 2007-10-24
I would like to write a script to accomplish this as well however when I run xrandr (with or without sudo) I get this result:

 xrandr
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  151 (RANDR)
  Minor opcode of failed request:  6 ()
  Serial number of failed request:  9
  Current serial number in output stream:  9

---

