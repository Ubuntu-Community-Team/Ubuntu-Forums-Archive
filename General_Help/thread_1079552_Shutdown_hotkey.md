---
title: "Shutdown hotkey"
date: 2009-02-24
forum: General Help
---

### Post by JamesFMC on 2009-02-24
I have Ubuntu on Compact Flash embedded in a medical device. Normally, users would just hold down the power button to turn off the device, but I would like to try and avoid improper shutdowns.

Is there any way that I can assign a hotkey (other than alt+ctrl+del) to shutdown Ubuntu automatically without displaying the shutdown/restart box?

---

### Post by ddrichardson on 2009-02-25
You could add an acpi event to /etc/acpi/events/power or /etc/acpi/events/powerbtn (I'm not sure which one Ubuntu uses, to assign an action to the power button.

A bit more looking seems that Ubuntu uses /etc/acpi/events/powerbtn to call /etc/acpi/events/powerbtn.sh so all you need do is amend it to shutdown the computer:
```
shutdown -h now
```Would shutdown immediately, replace now with a time in seconds for a delay.

---

### Post by unutbu on 2009-02-25
How does one associate key presses with acpi events?

---

### Post by ddrichardson on 2009-02-25
If its just to shutdown then use Gnome's keyboard shortcuts setup to associate with the command that calls the event, so map say Ctrl+S to "shutdown -h now".

This might be a good [place to start]("http://www.thinkwiki.org/wiki/How_to_get_special_keys_to_work#Triggering_key_events").

---

### Post by unutbu on 2009-02-25
Thank you for the link, ddrichardson.
For a generic desktop, is there something equivalent to the 
ibm-acpi/thinkpad-acpi events table shown in the link?

E.g.```


Fn F1 --> ibm/hotkey HKEY 00000080 00001001 
Fn F2 --> ibm/hotkey HKEY 00000080 00001002
```

etc.

---

