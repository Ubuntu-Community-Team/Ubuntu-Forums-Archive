---
title: "Same Seperator and Handle"
date: 2008-06-05
forum: Desktop Environments
---

### Post by twodayslate on 2008-06-05
I am trying to make the handle and the separator look that same but I am having trouble
```
	GtkPaned       ::handle-size          = 2
    			image
    				{
       					function		= VLINE
       					recolorable		= TRUE
       					file			= "Lines/line-v.png"
       					border			= { 0, 0, 1, 1 }
       					stretch			= TRUE
    				}
    			image
    				{
      					function		= HANDLE
       					recolorable		= TRUE
       					file			= "Lines/line-v.png"
       					border			= { 1, 0, 1, 1 }
       					overlay_stretch		= FALSE
      					orientation		= VERTICAL
    				}

``` [http://img111.imageshack.us/img111/3017/screenshotcm8.png](http://img111.imageshack.us/img111/3017/screenshotcm8.png)
I am off by 1 px

[http://ubuntuforums.org/showthread.php?t=818460](http://ubuntuforums.org/showthread.php?t=818460)

---

### Post by twodayslate on 2008-06-14
Anyone?

edit:// Figured it out. Make the handle image bigger

---

