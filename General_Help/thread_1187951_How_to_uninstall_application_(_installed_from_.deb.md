---
title: "How to uninstall application ( installed from .deb ) ?"
date: 2009-06-15
forum: General Help
---

### Post by ActiveFrost on 2009-06-15
Ok, so .. I thought it would be worth to try Picasa, but somehow, menu is not working and I need to remove it ( app without the menu is not an app :D ).
How I can remove it ( downloaded & installed from .deb ) ?

---

### Post by DeMus on 2009-06-15
> **ActiveFrost said:**
> Ok, so .. I thought it would be worth to try Picasa, but somehow, menu is not working and I need to remove it ( app without the menu is not an app :D ).
How I can remove it ( downloaded & installed from .deb ) ?

Can you find the program in Add/Remove? (Applications - Add/Remove)
Or open Synaptic (System - Administration - Synaptic)
In the search bar type the first characters of the name and see if it pops up with a green square at the beginning of the line. Click that square and select uninstall.

---

### Post by ActiveFrost on 2009-06-15
[COLOR="Silver"]Yes, I already tried it - 0 results in Add/Remove & Synaptic ! That's why I'm asking here.[/COLOR]

Sorry, my mistake .. actually I've recently found something called "python-gdata" which looks like Picasa ( description contains Google, images, etc. ). BUT - if I select it for removal, it prompts me for a confirmation of totem & totem-plugins removal. What was Totem ? Can I remove it ?

Update: My second mistake .. it's not Picasa :D SO, does anybody know how to remove it ?

---

### Post by nothingspecial on 2009-06-15
```
sudo dpkg -r name_of_app
```

---

### Post by ActiveFrost on 2009-06-15
Ok, finally - removed :
```
sudo aptitude remove picasa
```

Though, why I wasn't able to remove it by using apt-get remove or Add/Remove & Synaptic ?

---

