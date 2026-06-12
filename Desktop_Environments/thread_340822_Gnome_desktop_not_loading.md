---
title: "Gnome desktop not loading"
date: 2007-01-17
forum: Desktop Environments
---

### Post by viper on 2007-01-17
Just wondering if there is a command line way of changing an icon theme or going back to the default Edgy Human theme.
Some how in the Theme Details Icons tab window a mouse cursor theme was installed, when i was selecting a different icon theme to use i accidently clicked on the mouse cursor theme, then all the icons on the desktop disapeared.
Tried to reboot the pc and it just hangs at the splash screen.
Any help would be appreciated thanks.](*,)

---

### Post by ComplexNumber on 2007-01-17
both the gtk theme and icon theme are in /home/<your-username>/.gconf/desktop/gnome/interface. its an xml file.
i've never tried this before, but i suppose you couldedit it on the command line, then reboot or log out.
choose failsafe in GDM.

---

### Post by viper on 2007-01-17
ComplexNumber, your a legend m8 thanks for pointing me in the right place.:D

---

### Post by ComplexNumber on 2007-01-17
glad to help :).

---

### Post by Tyralon on 2007-01-18
I have this exact problem, and I'm kinda new to Linux so I have absolutely no idea what to do. How do I edit the xml file? 
I appreciate any help I can get. :)

---

### Post by ComplexNumber on 2007-01-18
> **Tyralon said:**
> I have this exact problem, and I'm kinda new to Linux so I have absolutely no idea what to do. How do I edit the xml file? 
I appreciate any help I can get. :)
do you mean  if you only have the command line as an option? its exactly the same as for a text file. an xml file is basically a text file structured in a certain way. somthing like this:
> <?xml version="1.0"?>
<title>
[COLOR=White]......[/COLOR]<name message>="this is an xml file"
[COLOR=White]......[/COLOR]</name>
</title>

---

