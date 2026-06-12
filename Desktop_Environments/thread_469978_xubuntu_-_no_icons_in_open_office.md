---
title: "xubuntu - no icons in open office"
date: 2007-06-10
forum: Desktop Environments
---

### Post by merlinus on 2007-06-10
Wondering why there are no Open Office toolbar icons (only text buttons) with xubuntu, as compared with ubuntu?

The same is true with Mousepad.

Thanks.

-merlin

---

### Post by ugm6hr on 2007-06-10
Not sure what you mean.  My OpenOffice works fine in Xubuntu7.04 (installed from repo).

---

### Post by merlinus on 2007-06-10
My version does not have the icons, only text (e.g. buttons that say bold, italic).  It is fine in Gnome.

I did not change any settings for the program.

:confused:

-merlin

---

### Post by ugm6hr on 2007-06-10
Have you changed your theme in Xubuntu?

I think the programs access icons from /usr/share/icons/Tango

Have a look in any of the folders (e.g. 24x24/actions/format-text-bold.png) to see if the icons are there.  If you have changed your theme, you may have to either link or copy from Tango to your theme icon folder.

---

### Post by floke on 2007-06-10
For some weird and profoundly stupid reason, sometimes the icons are not actually installed. What a great thing to do eh? Simply open synaptic, run a search for office -.. blah blah and install the icons.

---

### Post by merlinus on 2007-06-10
When I changed my icon theme back to gnome, everything went back to the way it was.

I also downloaded the crystal, tango and andromeda styles, so at least there is some choice.

Thanks to all!

-merlin

---

### Post by MeMosh on 2007-06-12
i have the same problem, i think it has something to do with the lack of icon themes, the program uses default icons but when u change.. say, your widow color to darker, the program seems to try to use accessibility icons (wich doesnt exist) so it shows anoying text instead, im gona try downloading any icon theme.

EDIT: 

Ohh, i see, when you cant see icons even when the style packages are installed, its because the view options are pointing to a nonexistent theme, i set it to default and my icons are back, for dark window color i had to install hi-contrast icons cuz u cant use any other theme with dark window colors.

---

### Post by chadwicktr on 2007-08-16
Thanks, I installed ubuntu, then the xubuntu desktop and had the same problem -- no icons just text. 

Just used synaptic package manager to **reinstall** the tango theme and it works great now. 

Thanks again!

---

### Post by Afkpuz on 2007-08-24
Here's the simple way.  This will install all the availible icon sets for openoffice.

```


sudo apt-get install openoffice.org-style-andromeda openoffice.org-style-crystal openoffice.org-style-default openoffice.org-style-hicontrast openoffice.org-style-human openoffice.org-style-industrial openoffice.org-style-tango


```

---

### Post by aashay on 2007-09-17
> **Afkpuz said:**
> Here's the simple way.  This will install all the availible icon sets for openoffice.

```


sudo apt-get install openoffice.org-style-andromeda openoffice.org-style-crystal openoffice.org-style-default openoffice.org-style-hicontrast openoffice.org-style-human openoffice.org-style-industrial openoffice.org-style-tango


```

worked like a charm.. however i now have ugly icons on the toolbars (looks like the high contrast theme)
Changing the iconsets in the OPTIONS does not do anything... any workarounds?

---

