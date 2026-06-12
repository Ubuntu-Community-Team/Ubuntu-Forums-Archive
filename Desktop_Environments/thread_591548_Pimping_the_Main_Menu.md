---
title: "Pimping the Main Menu?"
date: 2007-10-25
forum: Desktop Environments
---

### Post by rollerdiscoman on 2007-10-25
Hello,
Is there any way to make the menus different (better) looking so I dont have this Amazing taskbar, and then a bland, white menu?

thanks!

---

### Post by NilsE on 2007-10-25
> **rollerdiscoman said:**
> Hello,
Is there any way to make the menus different (better) looking so I dont have this Amazing taskbar, and then a bland, white menu?

thanks!
Menus can be changed with themes and other customizations

System>Preferences>Appearance

---

### Post by rollerdiscoman on 2007-10-25
That didnt work for me. I'm running Gutsy, and I need to make the menus look different.

System> Preferences> Appearance did nothing to help that.

---

### Post by NilsE on 2007-10-25
> **rollerdiscoman said:**
> That didnt work for me. I'm running Gutsy, and I need to make the menus look different.

System> Preferences> Appearance did nothing to help that.
You may not have any themes installed that make a change to the menus. You may want to hunt around for some themes or create your own. There are some themes in the repository like Crux that makes the menus light purple.   For example I created my own theme and my menus are chrome.

Also, you can pick subsets of the themes and the ones you want to tinker with are the ones under the customize>controls

---

### Post by rollerdiscoman on 2007-10-25
OO, how do you make your own themes? does that require any programming knowlege?

---

### Post by NilsE on 2007-10-25
> **rollerdiscoman said:**
> OO, how do you make your own themes? does that require any programming knowlege?
Not really it is along the lines of xml.

Go into /usr/share/themes and poke around in one of the themes. The gtk themes are the ones that change controls. Read the gtkrc file to get a feel for how they work.

Not all themes will have images so poke around until you find one that does so you can see how you can change things by just replacing an image.

---

