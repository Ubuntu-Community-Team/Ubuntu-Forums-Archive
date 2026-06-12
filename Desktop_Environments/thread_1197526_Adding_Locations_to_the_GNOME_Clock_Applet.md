---
title: "Adding Locations to the GNOME Clock Applet"
date: 2009-06-26
forum: Desktop Environments
---

### Post by fundae on 2009-06-26
Hi

How do I add new locations to location list in the GNOME clock applet? Is there a file I can edit somewhere. I want to add Bangalore, India to the list (ICAO code: VOBG) to the list. I'd like to file a bug, but I'm not sure where I should report it. Also, I'd be grateful if somebody could give me a quick fix that I could use until the bug is fixed.

On a side note its quite ridiculous that the applet doesn't have Bangalore which is one the largest cities in the world, but lists much smaller and nearly unheard of cities like Linkoping (no offence intended, I'm posting this message from Linkoping and its a very nice city with very nice people).

Thanks in advance,
Pramod

---

### Post by ronnyromero on 2010-02-23
i need to make a script that configures this clock applet, have you found a way to configure it without using the GUI?

---

### Post by mcduck on 2010-02-23
> **ronnyromero said:**
> i need to make a script that configures this clock applet, have you found a way to configure it without using the GUI?

You should have probably started your own thread, since your question isn't really related to the original question.

..but anyway, the clock applet stores it's locations in gconf, so if you need to change the settings from command line you can use gconftool-2 to do that.

The relevant gconf key is *apps/panel/applets/clock_screen0/prefs/cities*.

---

### Post by drewsus on 2010-11-09
I believe this would be the value you would want to set that key to:
```
[<location name="" city="Bangalore" timezone="Asia/Kolkata" latitude="12.949986" longitude="77.668205" code="VOBG" current="false"/>]
```

---

