---
title: "Character rendering issue on 9.04"
date: 2009-05-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by fromHungary on 2009-05-17
Hi Everyone,

I've just upgraded to 9.04 in two steps (first to 8.10, and then to 9.04)  on my pretty old Dell Latitude C400 laptop and my characters get corrupted from time to time to a level of becoming unreadable in the panel or in any application and certain artifacts appear even in case of images.
See the screenshot below:

[IMG]http://www.businessphoto.hu/images/ubuntu2.png[/IMG]


Do you have any idea what the reason cen be for this or how I could cure it?

Thanks a lot,
Tibor

---

### Post by sirebral on 2009-05-17
From time to time?  What are you doing before this happens?

---

### Post by superm1 on 2009-05-17
> **fromHungary said:**
> Hi Everyone,

I've just upgraded to 9.04 in two steps (first to 8.10, and then to 9.04)  on my pretty old Dell Latitude C400 laptop and my characters get corrupted from time to time to a level of becoming unreadable in the panel or in any application and certain artifacts appear even in case of images.
See the screenshot below:

[IMG]http://www.businessphoto.hu/images/ubuntu2.png[/IMG]


Do you have any idea what the reason cen be for this or how I could cure it?

Thanks a lot,
Tibor
For starters, try turning off compiz (desktop effects).  See if that cleans it up

---

### Post by fromHungary on 2009-05-18
> **sirebral said:**
> From time to time?  What are you doing before this happens?
I can do practically whatever I want, it happens. However, straight after booting it looks OK.

---

### Post by fromHungary on 2009-05-18
> **superm1 said:**
> For starters, try turning off compiz (desktop effects).  See if that cleans it up
Compiz is not switched on on this old and slow laptop.

---

### Post by fromHungary on 2009-05-18
> **fromHungary said:**
> Hi Everyone,

I've just upgraded to 9.04 in two steps (first to 8.10, and then to 9.04)  on my pretty old Dell Latitude C400 laptop and my characters get corrupted from time to time to a level of becoming unreadable in the panel or in any application and certain artifacts appear even in case of images.
See the screenshot below:

Do you have any idea what the reason cen be for this or how I could cure it?

Thanks a lot,
Tibor


I seem to have found the resolution **[here]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4")** (briefly it is installing the legacy Interpid Intel video driver). It looks working OK, however I would prefer keeping my system clean and using a more official solution.

---

### Post by RJJDallasGA on 2009-07-29
And I thought it was just me!  I'll try this tonight. My C400 is a great computer and I knew it had to be drivers in 9.04  BTW this happens with upgerade as well as a clean install.  

Thanks!
Ronny

---

