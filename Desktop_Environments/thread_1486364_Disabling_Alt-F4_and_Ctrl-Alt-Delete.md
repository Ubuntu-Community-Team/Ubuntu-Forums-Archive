---
title: "Disabling Alt-F4 and Ctrl-Alt-Delete"
date: 2010-05-17
forum: Desktop Environments
---

### Post by dmtrotter on 2010-05-17
I have built a custom LiveCD Kiosk from scratch using the Karmic sources. It is working very well, but I have a few issues I can not seem to get ironed out. I want to disable the Ctrl-Alt-Del altogether as well as Alt-F4. Both of these are causing issues with some people using the LiveCD.

What I have, and how it works:

LiveCD using Karmic as the core, and Fluxbox. The individual boots from the CD and is taken to a Fluxbox desktop where they only have 3 options:
   1. Work
   2. System Info
   3. Speed Test

1 - Takes them to our Citrix Web Interface (in kiosk mode) where they log in to gain access to their apps using the Citrix client (not Java)
2 - Launches Conky and displays some system info
3 - Launches a browser (in kiosk mode again) and takes them to a broadband speed test site.

The issue I have is them having the ability to close the Citrix client (Alt-F4). I want to disable this to force them to log out of the client correctly.

The other issue is when they hit Ctrl-Alt-Del, it logs them out and takes them to a login window. I want to remove this as well so they are forced to log out correctly. 

I have edited the /etc/init/control-alt.delete.conf file and commented out the task there, but that didnt help. I have also tried modifying the /usr/share/hal/fdi/policy/10osvendor/10-x11-input.fdi file and adding this line:
```
<merge key="input.xkb.options"  type="string">terminate:ctrl_alt_bksp</merge>
```
That has not helped either - maybe put it in the /etc/hal/fdi/policy/preferences.fdi file?

Any help and/or suggestions are greatly appreciated.

Cheers!

---

### Post by ubunterooster on 2010-05-17
system>preferences>keyboard shortcuts?

---

### Post by apporc on 2010-05-17
this may help you.

gnome-keybinding-properities

You will find Ctrl+Alt+Del is for 'logout' ,delete it then.

Help this can help you.

---

### Post by dmtrotter on 2010-05-18
> **ubunterooster said:**
> system>preferences>keyboard shortcuts?


This would help if I was building the LiveCD via a GUI, but all the work I have to do to configure it is done from the command line.

---

### Post by dmtrotter on 2010-05-18
> **apporc said:**
> this may help you.

gnome-keybinding-properities

You will find Ctrl+Alt+Del is for 'logout' ,delete it then.

Help this can help you.


Can this be done from the command line?

---

### Post by dmtrotter on 2010-06-17
Anyone? There has to be a way to accomplish this.

---

