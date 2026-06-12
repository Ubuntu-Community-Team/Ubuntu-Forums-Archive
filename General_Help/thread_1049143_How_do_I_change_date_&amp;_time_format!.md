---
title: "How do I change date &amp; time format!"
date: 2009-01-24
forum: General Help
---

### Post by josamoto on 2009-01-24
Just wanted to know how you can change the date/time format to for example something like DD/MM/YY HH:MM.

The clock display on the top right panel doesn't offer too many options for this, but I assume there's a config file somewhere I can change.

Thanks!!!

---

### Post by spiderbatdad on 2009-01-24
possibly like this: Open the configuration editor: Alt+f2. enter gconf-editor. Navigate to Apps>>panel>>applets>>clock_screen0>>prefs. Locate the item "custom_format" and highlight with left click. Now right click the item and select edit key. Input a value understood by strftime, as described here: [http://manpages.courier-mta.org/htmlman3/strftime.3.html](http://manpages.courier-mta.org/htmlman3/strftime.3.html)
I have not tested this.

---

### Post by josamoto on 2009-01-24
Hi thanks for the post, I tried changing the custom_format like you explained, and restarted, but it didn't work.

I also searched for other instances of custom_format, but there was only one.

Any other ideas?

---

### Post by josamoto on 2009-01-24
Tried again, I forgot to set format to 'custom', It's working now!!! Thanks!

---

### Post by spiderbatdad on 2009-01-25
I see I have tested this now and it works well. So in addition to changing the custom_format field to values from strftime. The format field gets editted from 12-hour to custom. Thanks to you as well, joint effort here.

---

### Post by FraggedLocust on 2009-02-23
Is it possible to push an algorithm into custom_format? I want to display the full julian date (i.e. 2500000.00000) and the julian date of the year isn't quite what I want.

---

### Post by Gingalone on 2009-05-14
> **spiderbatdad said:**
> possibly like this: Open the configuration editor: Alt+f2. enter gconf-editor. Navigate to Apps>>panel>>applets>>clock_screen0>>prefs. 


:?:
In my configuration editor that key (Apps>>panel>>applets>>clock_screen0) doesn't exist!
What can I do the change my system (Ubuntu Jaunty) date & time format?
Thanks for help,
Gingalone

---

