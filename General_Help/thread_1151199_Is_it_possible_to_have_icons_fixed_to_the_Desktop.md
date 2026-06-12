---
title: "Is it possible to have icons fixed to the Desktop?"
date: 2009-05-06
forum: General Help
---

### Post by toejamfootball on 2009-05-06
I only have two icons on my Desktop, they are 2 extra Hard Drives. When I boot up they are in a different position than I would like them to be. I was wondering is there a way I can put them where I like them, and then lock them in that position?

Here are two Screenshots to show the difference, in case I didn't make sense :)

At boot up - 

[[IMG]http://img139.imageshack.us/img139/6573/icons.th.png[/IMG]](http://img139.imageshack.us/my.php?image=icons.png)

How I like them - 

[[IMG]http://img239.imageshack.us/img239/586/screenshotmay.th.png[/IMG]](http://img239.imageshack.us/my.php?image=screenshotmay.png)

Cheers!

James.

---

### Post by dli8ilb on 2009-05-06
a couple things to try:
type gconf-editor in a terminal
navigate to apps>nautilus>icon_view

try checking:
default_use_manual_layout
and/or
default_use_manual_layout

i hope this helps :P

---

### Post by toejamfootball on 2009-05-06
> **dli8ilb said:**
> a couple things to try:
type gconf-editor in a terminal
navigate to apps>nautilus>icon_view

try checking:
default_use_manual_layout
and/or
default_use_manual_layout

i hope this helps :P
Ok cool, would I do this after I have moved the Icons to where I want them? Or doesn't it matter?

Thanks.

EDIT: That worked pretty well, they aren't as close together as I'd liked, but I can live with that. Thanks mate.

---

### Post by dli8ilb on 2009-05-06
sure thing friend :-) another thing you might try is right-clicking the icons and stretching them a bit.  it might fill up some empty space and lock them in place better.  also, in the same gconf location as mentioned before there's a default_zoom_level setting.  try changing it to one of these:

smallest (33%), smaller (50%), small (66%), standard (100%), large (150%), larger (200%), largest (400%)

---

### Post by sheel1234 on 2009-05-06
Yes, just drag the icons from your menu and it will automaticly fix to the desktop

---

### Post by toejamfootball on 2009-05-06
> **sheel1234 said:**
> Yes, just drag the icons from your menu and it will automaticly fix to the desktop
That just copies everything from the HDD to a folder on the Desktop.

---

