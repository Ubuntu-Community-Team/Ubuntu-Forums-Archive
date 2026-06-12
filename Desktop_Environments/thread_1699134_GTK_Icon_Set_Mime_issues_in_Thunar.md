---
title: "GTK Icon Set Mime issues in Thunar"
date: 2011-03-03
forum: Desktop Environments
---

### Post by beastrace91 on 2011-03-03
So this is the index.theme in my icon set is the following:

```
[Icon Theme]
Name=ReMix
Comment=Gnome-mixed source icon theme.
Inherits=Tango,gnome
Example=x-directory-normal

Directories=actions,apps,categories,devices,devices,emblems,mimetypes,places,status,spinner

[actions]
Size=128
Context=Actions
Type=Scalable

[apps]
Size=128
Context=Applications
Type=Scalable

[categories]
Size=128
Context=Categories
Type=Scalable

[devices]
Size=128
Context=Devices
Type=Scalable

[emblems]
Size=128
Context=Emblems
Type=Scalable

[places]
Size=128
Context=Places
Type=Scalable

[mimetypes]
Size=128
Context=MimeTypes
Type=Scalable

[spinner]
Size=22
Context=Applications
Type=scalable

[status]
Size=128
Context=Status
Type=Scalable

```

Any idea what in here would keep the mime icons from displaying right? The icon set works except for displaying the general folder icons in thunar (specific folder icons like documents, home, downloads all show up). According to [here](http://thunar.xfce.org/pwiki/documentation/faq) it means an issue with my mime icons... So - what is wrong?

For comparison here is the index.theme of a icon set that fully works: ```
[Icon Theme]
Name=Drakfire Evolution Inverted
Inherits=Tango,gnome,hicolor
Comment=Theme inspired by Meliae
Example=x-directory-normal
Directories=scalable/actions,scalable/apps,scalable/apps/48,scalable/spinner,scalable/places,scalable/mimetypes,scalable/devices,scalable/emblems,scalable/emblems/32,scalable/stock,scalable/stock/64,scalable/stock/48,scalable/stock/24,scalable/stock/22,scalable/stock/16,scalable/categories

[scalable/categories]
Size=128
Context=Categories
Type=scalable

[scalable/actions]
Size=128
Context=Actions
Type=scalable

[scalable/emblems]
Size=128
Context=Emblems
Type=scalable

[scalable/emblems/32]
Size=32
Context=Emblems
Type=scalable

[scalable/apps]
Size=128
Context=Applications
Type=scalable

[scalable/apps/48]
Size=48
Context=Applications
Type=scalable

[scalable/spinner]
Size=36
Context=Applications
Type=scalable

[scalable/devices]
Size=128
Context=Devices
Type=scalable

[scalable/places]
Size=128
Context=places
Type=scalable

[scalable/mimetypes]
Size=128
Context=MimeTypes
Type=scalable

[scalable/stock]
Size=32
Context=Stock
Type=scalable

[scalable/stock/64]
Size=64
Context=Stock
Type=scalable

[scalable/stock/48]
Size=48
Context=Stock
Type=scalable

[scalable/stock/24]
Size=24
Context=Stock
Type=scalable

[scalable/stock/22]
Size=22
Context=Stock
Type=scalable

[scalable/stock/16]
Size=16
Context=Stock
Type=scalable
``` I can't see what is different here... Help?

~Jeff

---

