---
title: "Menus in Open Office Disappeared."
date: 2009-01-12
forum: General Help
---

### Post by Eyore15 on 2009-01-12
I am running Ubuntu 8.10.

I cam home today and found tht all of my Open Office applications no longer had any text associated with any of the menu items. They have been replaced with an underline (__).  If I click on one of the underlines, the drop-down "menu" appears with the same underline instead of text.

I have completely removed the software, rebooted, then re-installed.  It has had no effect.

I've posted in an open office forum, but I thought someone here might be able to help as well.  

I've attached a screenshot so you can see it.

I'd appreciate any help that you can offer.

regards

mark c. miller

---

### Post by whoop on 2009-01-12
Try to remove the config directory in your user directory. On my installation it is called: /home/myusername/.openoffice.org2

---

### Post by Eyore15 on 2009-01-12
]Try to remove the config directory in your user directory. On my installation it is called: /home/myusername/.openoffice.org2

I removed /home/username/.openoffice.org2 with no effect.

I then removed /home/username/.openoffice.org and org2 with no effect.

I then removed a file called open office in my home directory.  no effect.

The software continues to function just fine; it's just that there is no menu text (and I can't remember all the options off the top of my head).

Thanks for the suggestion.  Might you have any others?

mcm

---

### Post by LowSky on 2009-01-12
have you change your theme?

change it back to clearlooks or the ubuntu standard, which name has escaped me at the moment

---

### Post by Eyore15 on 2009-01-12
> **LowSky said:**
> have you change your theme?

change it back to clearlooks or the ubuntu standard, which name has escaped me at the moment

Already tried that too.  I changed from clearlooks to one of the others -- no change; then I changed it back to clearlooks -- no change

---

### Post by Hagar Delest on 2009-01-17
Maybe this will help: [[Solved] No text in OpenOffice menus](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=10183).

---

### Post by abn91c on 2009-01-17
```
sudo apt-get remove openoffice.org-gnome
```

---

### Post by mike2357 on 2009-01-17
This problem seems to be caused by the interplay of openoffice, compiz and drivers for older Nvidia cards.  The solution is pretty simple, and easy to reverse if it doesn't work:  change your font setting as follows:

System -> Preferences -> Appearance -> Fonts

In the Rendering section, click on the "Subpixel smoothing (LCDs)" radio button.

---

### Post by jvnn on 2009-01-30
> **mike2357 said:**
> This problem seems to be caused by the interplay of openoffice, compiz and drivers for older Nvidia cards.  The solution is pretty simple, and easy to reverse if it doesn't work:  change your font setting as follows:

System -> Preferences -> Appearance -> Fonts

In the Rendering section, click on the "Subpixel smoothing (LCDs)" radio button.

Thank you - this worked perfectly for me.

---

