---
title: "steing up  Beryl"
date: 2007-06-04
forum: Desktop Effects &amp; Customization
---

### Post by BlackBar on 2007-06-04
I got beryl for the add/remove and now i have no idea what to do next  i looked at the settings and 
have no idea were to start can someone please tell to me the best way to set up beryl ie: wobbly windows cube effect ect... also i get this see attachment when trying to enable desktop effects

---

### Post by Inxsible on 2007-06-04
Did you also install the Beryl Manager ?

I would do this again:
```
 sudo aptitude install beryl beryl-manager
```
The Beryl Manager allows you to control your settings and also to start up.

---

### Post by BlackBar on 2007-06-04
yep i got it now can you help me set it up

---

### Post by BlackBar on 2007-06-05
Bump

---

### Post by B00R4dL3y on 2007-06-05
Search for setting up composite in xorg.conf for you video card.

---

### Post by BlackBar on 2007-06-05
[http://lists.freedesktop.org/archives/xorg/2005-April/007412.html](http://lists.freedesktop.org/archives/xorg/2005-April/007412.html)
like that im not sure what you meen i just dont know how to get he cube effect or anything to work when i use the short keys it dose nothing

---

### Post by Silenus on 2007-06-05
Beryl manager should be installed in system tools if not open up a terminal or start aptitude, and find the files and themes associated with beryl, they should be in the repositories, then you should start with the regular theme, and be able to add, if not check System > Preference for your beryl manager.

---

### Post by BlackBar on 2007-06-05
i have it installed i just don't know how to set it up the manager is there i have no idea what to do with it

---

### Post by Ub1476 on 2007-06-05
What is your graphic card?

The Xcomposite extension error means that you are not running in a XGL session. From that I suppose you have an ATI card..

First uninstall Beryl from add/remove.
Next, you need to do is to first follow this guide (if you have ATI): [Linky]("http://ubuntuguide.org/wiki/Ubuntu_Feisty#How_to_install_Beryl_.28ATI.29")
Scroll down to: Alternate method: Using closed source FGLRX drivers from ATI... and follow guide from there.

In case you have one of the ATI 9*** series you can follow the first guide, (AIGXL open source). Also I think the ATI xpress series should work with AIGXL, but I'm not sure.. 

In case you have Nvidia, use this guide..
[Link]("http://ubuntuguide.org/wiki/Ubuntu_Feisty#How_to_install_Beryl_.28Nvidia.29")

---

### Post by BlackBar on 2007-06-05
thanks i did what it said i have one problem i cant change my settings because my login window is offset the input box is far off to the bottom right and the background pic seems to be a a lower resolution then the rest of the screen

---

### Post by BlackBar on 2007-06-07
Bump

---

