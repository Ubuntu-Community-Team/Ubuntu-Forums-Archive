---
title: "Toggle visibility of Desktop icons"
date: 2010-05-24
forum: Desktop Environments
---

### Post by bobdobbs on 2010-05-24
Hi all.

I'm using gnome 2.30.0

I'd like to minimize distractions when I'm trying to focus on tasks while using GUI tools.

Can I toggle the visibility of the icons on the desktop?

Ideally, I'd like to click a button that will clear my visual desktop, so I can focus on what I'm doing. I'd like to be able to easily return visibility of my Desktop icons, so I can then visually navigate through my filesystem.

Is this possible ?

---

### Post by PhrankDaChickenGeek on 2010-05-24
Open a text file and paste the following
```


#!/bin/bash

STATUS=$(gconftool-2 --get /apps/nautilus/preferences/show_desktop)

if [ "$STATUS" == "false" ]; then
	gconftool-2 --set /apps/nautilus/preferences/show_desktop --type bool TRUE
else
	gconftool-2 --set /apps/nautilus/preferences/show_desktop --type bool FALSE
fi

```

Save it as toggle_desktop.sh
Right-Click on it, select Properties, select Permissions tab, and check Allow Executing file as program
Right click your panel and add a custom launch pointing to the script

---

### Post by bobdobbs on 2010-05-27
That works.
Thank you.

---

