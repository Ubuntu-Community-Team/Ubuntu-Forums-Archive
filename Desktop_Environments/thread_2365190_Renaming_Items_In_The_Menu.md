---
title: "Renaming Items In The Menu"
date: 2017-07-03
forum: Desktop Environments
---

### Post by Darth4212 on 2017-07-03
How would I go about renaming items in the menu.
Such as how Firefox and Google Chrome are called "Internet Browser" instead of their actual names. I want to use their actual names. I have tried Right Click, Edit Application but to no avail.

---

### Post by CatKiller on 2017-07-03
How far into the weeds do you want to get?

A quick-and-dirty method is to edit the appropriate .desktop files as root. They're probably in /usr/share/applications. They're just text files.

FWIW, for me, Firefox is listed as Firefox Web Browser, and Chrome is listed as Google Chrome. I don't know why it would be different for you.

---

### Post by Darth4212 on 2017-07-03
> **CatKiller said:**
> How far into the weeds do you want to get?

As far as need be.

> **CatKiller said:**
> A quick-and-dirty method is to edit the appropriate .desktop files as root. They're probably in /usr/share/applications. They're just text files.

Ok these edit the things in the menu. Just wondering since they are .desktop files and all

> **CatKiller said:**
> FWIW, for me, Firefox is listed as Firefox Web Browser, and Chrome is listed as Google Chrome. I don't know why it would be different for you.

It may be because I use Ubuntu Studio -idk why it's like that to be honest- but it has been that way since the beginning

---

### Post by CatKiller on 2017-07-03
> **Darth4212 said:**
> Ok these edit the things in the menu. Just wondering since they are .desktop files and all

Yes. The files are fairly straightforward in their layout. You may need to run update-menus afterwards to get the changes to appear.

The full and complicated tale of how you get from those files to actually having menu entries is [here]("https://www.freedesktop.org/wiki/Specifications/menu-spec/"). Also [here]("https://developer.gnome.org/menu-spec/").

Edit: possibly it's a trademark thing? I remember there was a thing in Debian called Iceweasel because of branding licensing problems a while back. Perhaps that's the reason why?

---

### Post by Dennis N on 2017-07-03
To get generic names in the Whisker Menu, there is a check box "show generic application names" under **Properties > Menu**. Most applications are affected; a few are not. Whisker uses the GenericName entry in the .desktop file if there is one. For Chromium,

**GenericName=Web Browser**

On my system, if the check box is checked, then both Firefox, and Chromium are labeled "Web Browser" (not "Internet Browser" like yours). If unchecked, then Firefox is labeled "Firefox" and Chromium is "Chromium". 

Right click on menu icon to get to "Properties".

---

### Post by Darth4212 on 2017-07-04
> **Dennis N said:**
> To get generic names in the Whisker Menu, there is a check box "show generic application names" under **Properties > Menu**.

Thank you! This fixed it!

---

### Post by Dennis N on 2017-07-04
Glad to help, and hope that you didn't get too far into the weeds.

---

### Post by Darth4212 on 2017-07-04
Wanted to thank you for your help too!!! May not have solved my problem but I know more now than I used to add it will definitely help me in the future!!

---

### Post by Darth4212 on 2017-07-04
> **Dennis N said:**
> Glad to help, and hope that you didn't get too far into the weeds.

Thankfully I didn't! But me being me I probably will end up going into the weeds sooner or later just for the hell of it!

---

