---
title: "Set Default Columns in Nautilus 3.26.4-0~ubuntu18.04.1"
date: 2018-10-10
forum: Desktop Environments
---

### Post by webusr1 on 2018-10-10
All,
Is there any way to setup Nautilus Visible Columns to stay configured after setting up more columns? Each time I include addition columns these settings are lost after closing Nautilus. And, these Visible Columns are not passed on to a new Nautilus window after setting them up in the current Nautilus window.  These settings are temporary only while Nautilus is running and are lost after closing Nautilus. It's a real hassle setting up visible columns every time I open a new instance of this file manager...

Any help would be greatly appreciated. I hope there is a way to make these settings stick. Also, if Nautilus 3.26.4 does not support keeping these settings, please let me know if there is another file manager that will work nicely with Ubuntu 18.04 as I don't want install a different file manager that cause more issues than it's worth... 

Thanks ahead of time.

Best Regards

---

### Post by DuckHook on 2018-10-10
> **webusr1 said:**
> …settings are temporary only while Nautilus is running and are lost after closing Nautilus.…
This is odd. On my system, which is exactly the same version as yours (OS and Nautilus), the column settings survive closing and reboot. How do you set your columns? Is it through Files &#8594; Preferences &#8594; List Columns ?

---

### Post by webusr1 on 2018-10-11
You are correct. Using the Preference from the Menu solved the problem. I was setting the visible columns from the icon settings at top right of window menu. Thanks so much!!!

Best Regards!

---

### Post by dougmccrary on 2018-11-04
Maybe you are using a different desktop, but I was able to edit /org/gnome/nautilus/list-view/default-visible-colums with dconf-editor to get what I wanted.

---

### Post by vanadium on 2018-11-05
> **dougmccrary said:**
> Maybe you are using a different desktop, but I was able to edit /org/gnome/nautilus/list-view/default-visible-colums with dconf-editor to get what I wanted.

Should you really be editing obscure config settings to achieve this? I think the workaround going through the preferences is a better workaround if it does not stick when using the icon on the menu. That said, even using the icon, the setting sticks for me.

---

