---
title: "Confirm the delete in Gnome"
date: 2007-01-19
forum: Desktop Environments
---

### Post by llelkes on 2007-01-19
Hi!

I am beginner with Ubuntu.
I'd like to ask to ask weather is it possible to set a delete function in Gnome to ask for confirmation all the time (move to trash or shift-delete).

Thanks,

llelkes

---

### Post by NESFreak on 2007-01-19
> **llelkes said:**
> Hi!

I am beginner with Ubuntu.
I'd like to ask to ask weather is it possible to set a delete function in Gnome to ask for confirmation all the time (move to trash or shift-delete).

Thanks,

llelkes

well there should be actually and it should be enabled by default.
go to the command line and enter
```
gconftool-2 -g /apps/nautilus/preferences/confirm_trash
```
if it gives you the value "false" then you should enter```
gconftool-2 -s /apps/nautilus/preferences/confirm_trash --type=bool true
```

else i wouldn't know what could be wrong.
NESFreak

---

### Post by cendant on 2007-02-22
> **NESFreak said:**
> well there should be actually and it should be enabled by default.
go to the command line and enter
```
gconftool-2 -g /apps/nautilus/preferences/confirm_trash
```
if it gives you the value "false" then you should enter```
gconftool-2 -s /apps/nautilus/preferences/confirm_trash --type=bool true
```

else i wouldn't know what could be wrong.
NESFreak

This is the only thing I hate about GNOME in Edgy. Very easy to delete something important without noticing.

Even though Confirm Trash is set to true (I checked visually in Gconf Editor), still you press Delete button and file is moved to the Trash without any warning.

Any ideas to fix it?

---

### Post by orb9220 on 2007-02-22
> This is the only thing I hate about GNOME in Edgy. Very easy to delete something important without noticing.

You can turn off the delete in right-click menu item in nautilus preferences.

---

### Post by cendant on 2007-02-23
> **orb9220 said:**
> You can turn off the delete in right-click menu item in nautilus preferences.

It still deletes without warning when I set it too warn me before deleting!

How does it behave for you in Edgy?

---

### Post by yitzle on 2008-04-25
I am using Debian etch and Gnome.
I used gconf-editor to toggle the value of /apps/nautilus/preferences/confirm_trash
At either value, I do NOT get asked for confirmation when deleting TO trash.
It, however, DOES affect whether I get a confirmation when I Shift+Del ie skip trash and delete the file for real, as well as whether I get a confirm when deleting something FROM the trash. So the label/description is broken.

---

