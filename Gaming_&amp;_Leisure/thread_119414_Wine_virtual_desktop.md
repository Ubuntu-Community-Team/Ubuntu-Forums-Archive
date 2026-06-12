---
title: "Wine virtual desktop"
date: 2006-01-19
forum: Gaming &amp; Leisure
---

### Post by link_36p on 2006-01-19
Most of my windows apps run fine without the virtual desktop accept half-life.
In the winecfg app I can turn the virtual desktop on, but it effects all apps run by wine, is the a peramiter i can launch half-life with so it will be in a virtual desktop even if its not turned on in the config file?

---

### Post by Somniis on 2006-10-28
Open up winecfg, and under the Application tab, click on "Add application...".  Browse to the half-life EXE and add it.  Click on the EXE name in the list, and set the virtual desktop for it to on.  This should fix your problem. :)

---

### Post by Paul_UK on 2006-11-05
The option is greyed when trying to configure a single app - it is only available when setting the default.  I have to run all my wine apps in a virtual desktop so I can use Dreamweaver 4 properly.  :(

---

### Post by hikaricore on 2006-11-05
> **link_36p said:**
> Most of my windows apps run fine without the virtual desktop accept half-life.
In the winecfg app I can turn the virtual desktop on, but it effects all apps run by wine, is the a peramiter i can launch half-life with so it will be in a virtual desktop even if its not turned on in the config file?

use this as your launcher for your program

```
wine explorer /desktop=hl,1024x768 c:\whereeverhalflifeis\halflife.exe
```

this will launch halflife with a virtual desktop and not affect other apps :)

i don't know the directory or the name of your halflife exe file so you need to adjust that info, also change 1024x768 to whatever size desktop you need.

hope this help.

--aaron

---

