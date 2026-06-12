---
title: "Nautilus 2.32.0 - List View - Set Default Columns"
date: 2010-12-20
forum: Desktop Environments
---

### Post by AnotherMuggle on 2010-12-20
I like view file listings in Nautilus in the List View.  By default the "Location" column is not visible and I have to set it to visible through "View -> Visible Columns" each time.  Is there anyway to make the change permanent? 

Cheers,
Tom

---

### Post by squid636 on 2011-02-10
Open a terminal and enter
```
gconf-editor
```
Navigate to /apps/nautilus/list_view and then double click on default visible columns
Add the entry 
```
location
```
to the list and close the box.
Close configuration editor.
Close ALL open windows of Nautilus.  Restart Nautilus by entering
```
sudo killall nautilus
```
in the terminal window. Wait until Nautilus finishes restarting before attempting to check on your changes.

---

### Post by Krytarik on 2011-02-10
Or just "Edit -> Preferences -> List Columns", tick "Location". ;-)

---

### Post by homeless36 on 2011-02-11
@ squid : thanks for the information .. :) ...

---

### Post by MichaelGld on 2011-04-09
> **squid636 said:**
> Open a terminal and enter
```
gconf-editor
```Navigate to /apps/nautilus/list_view and then double click on default visible columns
Add the entry 
```
location
```to the list and close the box.
Close configuration editor.
Close ALL open windows of Nautilus.  Restart Nautilus by entering
```
sudo killall nautilus
```in the terminal window. Wait until Nautilus finishes restarting before attempting to check on your changes.

Great tip. I tried it and it worked **except** for one column - image size. Any idea why that column won't add? 

Also, is there any way to use your method on a folder-by-folder basis? For example, in my Music folder, I want to always display bitrate and length, but not in non-music related folders.

MichaelGld

---

