---
title: "The Desktop problem"
date: 2009-04-26
forum: General Help
---

### Post by Thrashard on 2009-04-26
I accidentally renamed Desktop folder and then it started to show Home Folder files on my desktop. I renamed it back but it still shows Home files and folders. How can i fix it?

---

### Post by Tim Sharitt on 2009-04-26
First, I am going to assume that you have restored the name of ~/Desktop (capitalization does matter). If not, do that first.
 
Next, open gconf-editor (Hit Alt-F2 and enter gconf-editor). Go to / > apps > nautilus > preferences and make sure the box beside 'desktop_is_home_dir' is not checked.

---

### Post by Thrashard on 2009-04-26
I just have renamed Desktop folder when i was browsing it. If I want to start gconf-editor it shows me Error table: > Could not open location 'file:///home/arnas/gnconf-editor'

 Error stating file '/home/arnas/gnconf-editor': No such file or directory

---

### Post by Tim Sharitt on 2009-04-26
> **Thrashard said:**
> I just have renamed Desktop folder when i was browsing it. If I want to start gconf-editor it shows me Error table:
> Could not open location 'file:///home/arnas/gnconf-editor'

Error stating file '/home/arnas/gnconf-editor': No such file or directory



If that is the exact error message, check your spelling. :P

---

### Post by Thrashard on 2009-04-27
Yes, i fixed my spelling but it doesn't help. :/

---

