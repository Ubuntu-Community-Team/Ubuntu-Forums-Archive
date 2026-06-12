---
title: "Cannot enable compiz"
date: 2009-04-02
forum: Desktop Environments
---

### Post by chainsinthewall on 2009-04-02
Technically I'm a linux mint user, but from what I've read, its 94% ubuntu, so I figured I would try my luck here.

I have been trying for a couple of days to enable compiz on my laptop, but when I try, no go. I am trying to enable it through the Visual Effects tab of Appearance. 

This isn't a really big problem, but I do love compiz and would like to get it working.

EDIT: I am using an Nvida GeForce Go 6150. I have installed the restricted drivers.

---

### Post by Therion on 2009-04-02
What kind of graphics card or integrated graphics chipset do you have in your laptop?  

Not all chipsets support Compiz-Fusion.

---

### Post by chainsinthewall on 2009-04-02
sorry, should have posted that. I am using an Nvidia Geforce Go 6150. I know it supports Compiz because I used ubuntu on here about a year ago and Compiz worked fine.

---

### Post by Cybie257 on 2009-04-02
I have an ATI card and had a problem with compiz with the proprietary drivers vs OpenSource. 

I have dual monitors, so that even complicated more with the ATI drivers. 

my point: try using the other if available. Not to familiar with the nVidia options. 

-Cybie

---

### Post by mocoloco on 2009-04-02
I've had problems where I've messed up compiz with my tinkering.  Go in to ~/.gconf/apps (Open your home folder, hit Ctrl+L, type or paste that in).  Delete the compiz folder in there.  Log out and back in, then try enabling desktop effects again.

---

### Post by chainsinthewall on 2009-04-02
> **mocoloco said:**
> I've had problems where I've messed up compiz with my tinkering.  Go in to ~/.gconf/apps (Open your home folder, hit Ctrl+L, type or paste that in).  Delete the compiz folder in there.  Log out and back in, then try enabling desktop effects again.
No luck with that, unfortunatly.

---

### Post by Therion on 2009-04-02
> **chainsinthewall said:**
> sorry, should have posted that. I am using an Nvidia Geforce Go 6150. 
And you have the nVidia Restricted Driver enabled in the Hardware Driver Manager?

---

### Post by scubabuddy on 2009-04-02
I'm having a very similar problem with ubuntu Intrepid, except that compiz worked, then i shut my computer down for a week over spring break, came back to it and it doesn't work. I get the "Desktop effects could not be enabled" error when i try to use normal or extra in the visual effects tab of appearance (it was previously set to extra and running fine)

typing compiz in terminal gives:
```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 
Window manager warning: "" found in configuration database is not a valid value for keybinding "panel_main_menu"


```

---

### Post by chainsinthewall on 2009-04-02
> **Therion said:**
> And you have the nVidia Restricted Driver enabled in the Hardware Driver Manager?

Yes, I have installed them through both the Restricted Drivers gui, and envy from the terminal.

---

