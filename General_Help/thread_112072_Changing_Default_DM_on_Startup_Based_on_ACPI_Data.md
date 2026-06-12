---
title: "Changing Default DM on Startup Based on ACPI Data"
date: 2006-01-03
forum: General Help
---

### Post by xtacocorex on 2006-01-03
This probably should be posted in the laptops or programming section, but maybe not. 

I know how to check for the battery state as I have used it in another script.

I want to be able to have KDM switch the default desktop depending on whether my laptop is plugged in or running on battery in an attempt to conserve battery power. This way, I wouldn't have to select it in the sessions button on KDM.

For instance, powered would be KDE, on battery, something lighter like Fluxbox.

When I ran Fedora, it was easy to change the default desktop, by adding 
```

DESKTOP=<desktop of choice>

``` 
in a file (forgot the file, but I can easily dig it up when I get home as I think I bookmarked that page).

I'm currently searching around my Kubuntu install on my VMPlayer at work, but I can't find anything. I have found where I can change KDM to GDM if I so choose, but that's not what I'm looking for.

---

### Post by xtacocorex on 2006-01-04
^bump

This might be easier to answer, what are the system variables defining what desktop is chosen through KDM and where are they set. I couldn't find them in my search yesterday.

---

### Post by xtacocorex on 2006-01-05
After some experimenting, I've come to the conclusion that this is probably easiest done with a hack on KDM, but I'm still determined to figure this out. 

Does anyone know what file sets the DESKTOP_SESSION variable?

---

