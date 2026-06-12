---
title: "Mounted stuffs on the desktop"
date: 2010-10-19
forum: Desktop Environments
---

### Post by lovo on 2010-10-19
Hi everyone,
I would like to remove from my desktop the folder that are mounted (automatically I mount the Home folder). I tried in gconf-editor without success. Im using ubuntu 10.10
Can you help me ?
swan

---

### Post by tnat on 2010-10-19
Hi,

gconf-editor: /apps/nautilus/desktop/volumes_visible uncheck!

---

### Post by lovo on 2010-10-19
> **tnat said:**
> Hi,

gconf-editor: /apps/nautilus/desktop/volumes_visible uncheck!

As I said, I tried, see:
[IMG]http://img233.imageshack.us/img233/8110/screenshotgk.png[/IMG]

It is unchecked!!

I am looking for another way if it exists ..

---

### Post by mainerror on 2010-10-19
Try Ubuntu-Tweak. You can disable that feature and do many other interesting things.

---

### Post by lovo on 2010-10-19
There is the same option that is unchecked already ... :/

I mounted my disk with /etc/fstab, and all folders inside my home are displayed.

---

### Post by mainerror on 2010-10-19
Hold on. The content of your home folder is displayed on the desktop?

If so the your home folder might be set as desktop. In that case you can use gTweakUI - Nautilus and un-check the last option "Use home folder as desktop".

---

### Post by rogerdean on 2010-10-20
Hi tnat

Thanks for this - "gconf-editor: /apps/nautilus/desktop/volumes_visible uncheck!"

Is there a line I can paste into the terminal to do the same thing I wonder?

Many thanks again
Roger

---

### Post by stinkeye on 2010-10-20
> **rogerdean said:**
> Hi tnat

Thanks for this - "gconf-editor: /apps/nautilus/desktop/volumes_visible uncheck!"

Is there a line I can paste into the terminal to do the same thing I wonder?

Many thanks again
Roger

```
gconftool-2 --set /apps/nautilus/desktop/volumes_visible --type bool false
```

You could even make yourself a toggle_volumes_visible launcher in the panel.
Save this script as **toggle_volumes_visible** and make executable.
```
#!/bin/bash

STATUS=$(gconftool-2 --get /apps/nautilus/desktop/volumes_visible)

if [ "$STATUS" == "false" ]

    then gconftool-2 --set /apps/nautilus/desktop/volumes_visible --type bool TRUE

    else gconftool-2 --set /apps/nautilus/desktop/volumes_visible --type bool FALSE
fi

```

Right click panel 
add to panel > custom application launcher
and browse to the **toggle_volumes_visible** script for the command.

---

### Post by rogerdean on 2010-10-20
perfect, thanks very much...

---

### Post by lovo on 2010-10-20
> **mainerror said:**
> Hold on. The content of your home folder is displayed on the desktop?

If so the your home folder might be set as desktop. In that case you can use gTweakUI - Nautilus and un-check the last option "Use home folder as desktop".

I tried to install gTweakIU, but during the ./configure I have "Package libgnomeui-2.0 was not found in the pkg-config search path."

---

### Post by stinkeye on 2010-10-20
Open gconf-editor and navigate to /apps/nautilus/preferences/desktop_is_home_dir
and unmark.

---

### Post by lovo on 2010-10-20
> **stinkeye said:**
> Open gconf-editor and navigate to /apps/nautilus/preferences/desktop_is_home_dir
and unmark.

It is already unchecked. I think the problem comes from the fact I mount home with my fstab.

---

