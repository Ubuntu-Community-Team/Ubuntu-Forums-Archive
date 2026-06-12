---
title: "fast help with renameing xorg"
date: 2005-12-21
forum: Desktop Environments
---

### Post by syklitengutt on 2005-12-21
Hi. I changed something in my xorg.con file and renamed the old file to xorgback21.conf

x chrashed and I try to rename xorg.conf
to something else to change xorgback21 to xorg but Im not allowed.
Restricded or something.

The command I used is rename xorg.conf xorgaaa.conf

I tried with sudo first and as su

---

### Post by codejunkie on 2005-12-21
[QUOTE=syklitengutt]Hi. I changed something in my xorg.con file and renamed the old file to xorgback21.conf

x chrashed and I try to rename xorg.conf
to something else to change xorgback21 to xorg but Im not allowed.
Restricded or something.

The command I used is rename xorg.conf xorgaaa.conf

I tried with sudo first and as su[/QUOTE]
open the file in nano ```
sudo nano xorgwhatyounamedit.conf
```and press ctrl+o to save it and change the name back press enter to save it and the press ctrl+x to exit nano see if that helps.

---

### Post by syklitengutt on 2005-12-21
tnx...
that did it...
should have thought of that!

---

### Post by codejunkie on 2005-12-21
[QUOTE=syklitengutt]tnx...
that did it...
should have thought of that![/QUOTE]
glad to help.

---

### Post by frodon on 2005-12-21
I would overwrite my current xorg.conf with the old one if i was you : ```
sudo cp /etc/X11/xorgback21.conf /etc/X11/xorg.conf
```I think it's the easiest way to get back a good xorg.conf, you should try it next time ;)

---

