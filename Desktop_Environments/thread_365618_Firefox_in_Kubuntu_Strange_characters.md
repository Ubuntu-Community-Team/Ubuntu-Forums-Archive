---
title: "Firefox in Kubuntu: Strange characters"
date: 2007-02-19
forum: Desktop Environments
---

### Post by AusIV4 on 2007-02-19
Hi,
I have three computers, all three running Kubuntu. One of them is a clean install of Kubuntu, the other two were installed as Ubuntu, then I did ```
sudo aptitude install kubuntu-desktop
```On the two that have gnome installed, Firefox handles the unusual characters fine, but on the one that was a clean install, Firefox displays them as diamonds with question marks inside them, but Konqueror shows them as they are supposed to be. 

Here is one of the characters: &#65533;. I don't know if it will appear as the question mark for everyone, or if it will appear as an accented u for those with the proper fonts. I don't want to give up firefox for Konqueror because of these characters, and I don't want to install Ubuntu-desktop either. Is there any font package I can install to get things to display correctly?

---

### Post by ubix on 2007-02-19
In Firefox select ```
View -> Character Encoding -> Western(ISO 8859-1)
``` If this doesnt work select a different (a more international **[COLOR="Blue"]Unicode ( UTF-8 )[/COLOR]**) character set ```
View -> Character Encoding -> Unicode ( UTF-8 ) 
```

---

### Post by lhtown on 2007-02-19
You could try to set auto-detect as off under View>Character encoding in Firefox. Most web pages should automatically direct your browser as to what encoding to use to render the pages.

What languages are you using?

---

### Post by AusIV4 on 2007-02-21
Auto detect did it. I was using western.

Thanks.

---

