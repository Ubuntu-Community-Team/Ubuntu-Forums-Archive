---
title: "Getting rid of drive icons"
date: 2009-01-14
forum: General Help
---

### Post by kcode on 2009-01-14
Hey,
Whenever I mount any drive on my filesystem, the drive's icon appears on the desktop. I don't want this as i feel that I can very easily access them(drives) from Places menu. I'm using Gnome desktop environment and Ubuntu 8.04.

Thanks

---

### Post by logos34 on 2009-01-14
run this

> gconftool-2 --type boolean --set /apps/nautilus/desktop/volumes_visible 
"false"

---

### Post by kcode on 2009-01-14
> **logos34 said:**
> run this

Thanks

---

### Post by logos34 on 2009-01-14
glad to help

->thread tools>'mark as solved'

enjoy

---

### Post by kcode on 2009-01-14
> **logos34 said:**
> glad to help

->thread tools>'mark as solved'

enjoy

Hey,
I actually wanted to do this and also tag you with a thank, but couldn't see the corresponding links in the Ubuntu forums page. This is since yesterday, when the site went for repair.

Keep Shining :-)

---

### Post by logos34 on 2009-01-14
thanks,

yeah the site/servers are all screwed up...never been this bad

---

