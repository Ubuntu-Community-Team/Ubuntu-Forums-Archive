---
title: "Should these be on a menu or do I do it somehow?"
date: 2008-01-25
forum: Desktop Environments
---

### Post by SkipT on 2008-01-25
I'm new to Ubuntu so this may be obvious to others while it goes past me like a rocket.

I have Ubuntu 7.10 installed.  When I install programs from Synaptic Package Manager, they install but I don't find them on a menu anywhere.  Should they be on a menu or is this something I must chase down and somehow add them to a menu?

Thanks,
Skip

---

### Post by Samhain13 on 2008-01-25
It depends on what applications you installed.

---

### Post by Charcoal1981 on 2008-01-25
It depends what you are installing. If the app is command line only then it won't be added to the menu, same if it's a library or some other supporting file (you wouldn't want your menu cluttered with these). You can add items to the menu by going to 'Preferences > Main Menu > Add new item'.

Do you have an example??

---

### Post by freddyp on 2008-01-25
In my experience most applications add them.  Sometimes you might need to right click on Applications, select Edit Menus, and then find the new application and make sure it's checked so it's added to the Applications drop down menu.  Hope this helps!

---

### Post by SkipT on 2008-01-25
> **Charcoal1981 said:**
> It depends what you are installing. If the app is command line only then it won't be added to the menu, same if it's a library or some other supporting file (you wouldn't want your menu cluttered with these). You can add items to the menu by going to 'Preferences > Main Menu > Add new item'.

Do you have an example??
Thanks for the reply!

How does one tell if it's command line or not?  Most of them were in the Amateur Radio section. They show as installed in Synaptic but not in the add/remove program area of the application menu.

---

### Post by SkipT on 2008-01-25
> **freddyp said:**
> In my experience most applications add them.  Sometimes you might need to right click on Applications, select Edit Menus, and then find the new application and make sure it's checked so it's added to the Applications drop down menu.  Hope this helps!

They don't show in any of these menus.

Thanks!
Skip

---

### Post by SkipT on 2008-01-25
> **Samhain13 said:**
> It depends on what applications you installed.

1) Antennavis
2) gcb
3) gpredict
4) hamradiomenus
5) morse-x
6) yagi-uda

From what I've been able to determine via 'properties', these all appear to be command line driven.

Thanks to everyone for your time and pointing me to where I could find this out!

Skip

---

### Post by urukrama on 2008-01-26
Another way to find out: Open a terminal and type "man *nameoftheapplciation*" and you will be able to read the manual pages of the application (press q to exit). If it is not a command line application, it will most probably mention it.

---

### Post by Charcoal1981 on 2008-01-27
> **SkipT said:**
> Thanks for the reply!

How does one tell if it's command line or not?  Most of them were in the Amateur Radio section. They show as installed in Synaptic but not in the add/remove program area of the application menu.

I don't have any experience of any of the apps in that section. Synaptic gives a brief description of the app when you select it, which may or may not mention whether it is GUI or CLI. You could also try looking at the projects home page (if there is one. sometimes this is given in the description shown by synaptic). If you can't find info via synaptic try googling the package name to find out more.

---

