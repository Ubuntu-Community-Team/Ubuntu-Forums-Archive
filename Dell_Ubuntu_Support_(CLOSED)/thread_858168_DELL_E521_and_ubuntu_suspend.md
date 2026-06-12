---
title: "DELL E521 and ubuntu suspend"
date: 2008-07-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by cyclobs on 2008-07-13
hey guys,

when ever i try to suspend my ubuntu install it never suspends properly and i am unable to bring my computer out of suspend without needing to turn off my computer,

i am running a Dell E521, is this a common problem for this model or is it just me? :(

and also, is there a fix for this to work properly

---

### Post by jslate on 2008-08-18
Here's what I did that worked on my new DELL Latitude D630:

[LIST=1]
[*]Open Terminal
[*]Run the command 'sudo gedit /etc/default/acpi-support'
[*]Change the value for ACPI_SLEEP_MODE from "mem" to "standby" (without the quotes).
[*]Save and close the file.
[/LIST]

This did the trick. According to the comment above the property, "This will save less power, but may work on more machines." 

I got to the solution after visiting this thread, and upon examining the acpi-support file I decided to try the solution in the comments before making other changes, so I never made any of the changes noted in the thread.
[http://boulderjams.wordpress.com/2007/02/20/ubuntu-dell-suspend-fix/](http://boulderjams.wordpress.com/2007/02/20/ubuntu-dell-suspend-fix/)


Hope this helps.

---

