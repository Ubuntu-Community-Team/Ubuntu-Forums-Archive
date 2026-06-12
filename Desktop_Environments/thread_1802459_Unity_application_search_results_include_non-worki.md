---
title: "Unity application search results include non-working shortcuts"
date: 2011-07-12
forum: Desktop Environments
---

### Post by iamroddo on 2011-07-12
I'm running Ubuntu 11.4. I've played with different versions of Picasa, installing the Linux version via Ubuntu Software Center and also using Wine. At a certain point I had several versions of the application installed and things were getting. When I search for Picasa in the Unity application search field (clicking the button with the dot in the centre at the top left of my screen) I got several results for Picasa, some of which when clicked would start Picasa and some which wouldn't. When I remove all versions of Picasa both from Wine and native I still get some results for Picasa which don't start Picasa when clicked. How do I get rid of these from search results?

---

### Post by Krytarik on 2011-07-12
Check if there remained some in "~/.local/share/applications".

Greetings.

---

### Post by iamroddo on 2011-07-12
> **Krytarik said:**
> Check if there remained some in "~/.local/share/applications".


There were a few files with names related to some deleted apps. I moved them all to the Trash and found that my issue was now solved. Thanks!

---

