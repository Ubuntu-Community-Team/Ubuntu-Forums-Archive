---
title: "Dark themes: menu not affected"
date: 2017-12-25
forum: Desktop Environments
---

### Post by omnivore2000 on 2017-12-25
I've scoured the web a bit to see if this is even supposed to be possible in Lubuntu, apologies if I simply have this wrong.
I've used customize look and feel and the openbox config thing, it appears to me from screenshots like dark themes should make the menu and panel change appearance as well but they don't seem to affect it! 
Any help or direction here is greatly appreciated.
Linux noob

---

### Post by vasa1 on 2017-12-25
> **omnivore2000 said:**
> I've scoured the web a bit to see if this is even supposed to be possible in Lubuntu, apologies if I simply have this wrong.
I've used customize look and feel and the openbox config thing, it appears to me from screenshots like dark themes should make the menu and panel change appearance as well but they don't seem to affect it! 
Any help or direction here is greatly appreciated.
Linux noob
IIRC, you can edit the Openbox theme's themerc. Here's mine from way back:
```
border.width: 1
menu.border.width: 0
!#also applies to right-click menu
menu.title.bg: solid flat
menu.title.bg.color: #333333
menu.title.text.color: #aaaaaa

menu.items.active.bg.color: #101010
menu.items.active.bg: solid flat
menu.items.active.text.color: #aaaaaa
menu.items.bg.color: #252525
menu.items.bg: flat solid
menu.items.disabled.text.color: #888888
menu.items.text.color: #aaaaaa
menu.overlap: 0

padding.width: 3

*.text.justify: center
window.active.border.color: #111111
window.active.label.bg: parentrelative
!#window.active.label.text.color: #7F922C
!#window.active.label.text.color: #5BB757
!#window.active.label.text.color: #999999
!#window.active.label.text.color: #D8AF78
window.active.label.text.color: #000d1a
window.active.title.bg: Gradient Vertical Flat
window.active.title.bg.color: #222222
window.active.title.bg.colorTo: #555555
window.active.title.separator.color: #353535

window.*.client.color: #555555
window.client.padding.height: 0
window.client.padding.width: 0
window.*.grip.bg: parentrelative

!# Here width means thickness
window.handle.width: 5

window.inactive.border.color: #555555
window.inactive.label.bg: parentrelative
window.inactive.label.text.color: #777777
window.inactive.title.bg.color: #444444
window.inactive.title.bg: solid flat
!#window.inactive.title.separator.color: #8c8c8c
window.inactive.title.separator.color: #353535

window.active.handle.bg: Flat Border Solid
window.active.handle.bg.color: #444444
window.active.handle.bg.border.color: #444444
window.active.grip.bg: Flat Border Solid
window.active.grip.bg.color: #777777
window.active.grip.bg.border.color: #777777

```

---

### Post by omnivore2000 on 2017-12-25
Thank you very much for the reply, I'll have a tinker with it. Cheers

---

