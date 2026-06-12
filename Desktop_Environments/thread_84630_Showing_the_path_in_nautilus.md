---
title: "Showing the path in nautilus"
date: 2005-10-31
forum: Desktop Environments
---

### Post by sarah_b on 2005-10-31
I would like the nautilus file browser to show the complete path in a window so one can copy and paste it into a terminal, but I can not find a option to do this. Now for me it just shows tabs of what directory I'm in. I am using 5.10

If I remember correctly, in 5.04 my nautilus did do such a thing so I am thinking there is a setting I am missing.

Does anyone have knowledge of setting it up this way ?

sarah

---

### Post by suRoot on 2005-10-31
Open gconf (applications -> system tools -> configuration editor), navigate to apps-> nautilus -> preferences

Set always_use_location_entry to true

---

### Post by Sianis on 2005-10-31
It's working! Thank you!

---

### Post by OBnascar on 2005-10-31
[QUOTE=suRoot]Set always_use_location_entry to true[/QUOTE]

Unfortunately, my nautilus > preferences does not have the above options.
Any ideas ?

---

### Post by sarah_b on 2005-10-31
I can not find that path either in preferences, exact same problem as obnascar posted.

sarah

---

### Post by suRoot on 2005-10-31
See screenshot...

Try to add a new key under nautilus -> preferences

Right-click the right pane (where the other keys are listed) and select "New Key"

Name:  always_use_location_entry
Type:  Boolean
Value:  True

See if that works.

---

### Post by sarah_b on 2005-10-31
suRoot,

That was a great "how-to", now I have the full path displayed, thank you !

sarah

---

