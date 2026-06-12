---
title: "Printer missing in XSane"
date: 2006-06-11
forum: Desktop Environments
---

### Post by shane_on_u on 2006-06-11
I recently upgraded to Ubuntu 6.06. I'm having a problem with XSane, it doesn't seem to recognize my printer.

When I using 5.10 I had a heck of a time getting my scanner installed but XSane seemed to have no issue finding my printer. Now I seem to be the other way around, scanner detected automatically, but no printers found.

It does provide me with an option to add a new printer, but I can't seem to figure that screen out. Anyone have an idea as to what is going on?

---

### Post by shane_on_u on 2006-06-12
sorry about the bump... but anyone have any ideas? I can't figure this one out.

---

### Post by codypumper on 2006-06-12
I've had several problems with xsane, including one dealing with the plug-in for GIMP.  I fixed it by simply reinstalling it. If you haven't tried that, go to synaptic package manager, search sane then check xsane-common for reinstallation (do not uninstall it).

---

### Post by shane_on_u on 2006-06-12
Thanks for the suggestion. I have tried what you suggested and reinstalled again just to make sure but still no luck. Maybe some screenshots are in order. In the first shot, the area that I've circled, normally had my printer listed. Now it provides me with an option to add a printer (see second screenshot) but I haven't been able to figure out the correct values to enter here. Does anyone know how I can manually add a printer? The default values in this form don't work for me.

---

### Post by shane_on_u on 2006-06-12
sorry dont' know what happened to the screenshots... here they are

---

### Post by codypumper on 2006-06-13
what kind of printer is it?

---

### Post by shane_on_u on 2006-06-13
It's a Samsung ML-1740. The printer works otherwise, it's just that Xsane doesn't seem to detect it. I should probably also mention that it's connected to a print server.

---

### Post by codypumper on 2006-06-13
That could be part of the problem. Can you try connecting it directly to your computer and seeing if it works?

---

### Post by shane_on_u on 2006-06-13
Just tried without the print server... still the same. Printer detects fine... all programs except for XSane are able to use it. Weird.

---

### Post by codypumper on 2006-06-13
Your best bet is to hope for a patch/update.

---

### Post by shane_on_u on 2006-06-14
Yeah I had a feeling I was out of luck. Thanks for your help.

---

