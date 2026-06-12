---
title: "Firefox plug-in not working!!!!!!!!!!!!"
date: 2009-03-04
forum: General Help
---

### Post by psom on 2009-03-04
When im using firefox  in Ubuntu 8.10 and watching a video on, lets say, youtube I can hear nothing!! I have installed and uninstalled the plug-in (Shockwave Flash 10.0r15)but nothing happens... Any help??

Thanks

Psom

---

### Post by Therion on 2009-03-04
Other than in Firefox is your sound working normally?

---

### Post by psom on 2009-03-04
Yes it does.

---

### Post by Therion on 2009-03-04
Open Synaptic Package Manager.
Search on **gstreamer**.
Install the gstreamer codec packages (there will be a few of them (good, bad, ugly, etc.))
Restart Firefox/Youtube.


**Edit:**  Forgot to mention this previously but while you've got Synaptic open search for, and install, the **libflashsupport** package.


Joy?

---

### Post by psom on 2009-03-04
Should I install all of the packages??

---

### Post by Therion on 2009-03-04
Install the gstreamer **codec** packages.

---

### Post by psom on 2009-03-06
Still not working...

---

### Post by Therion on 2009-03-06
Search Synaptic for "gnash" and remove it if you have it installed.

If that doesn't work I'm out of ideas.

---

