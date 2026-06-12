---
title: "Avant Window Navigator 3d Effect Problem!!!!"
date: 2010-09-14
forum: Desktop Environments
---

### Post by unfoldedtoast on 2010-09-14
Hello everyone,

I  am kinda new to linux and avant window navigator is my first dock and im having some  trouble. It seems to have fully installed but it does not look very 3D.  specifically there is a white box surrounding it >_< any help  would be appreciated.

Thank you

:D

---

### Post by kerry_s on 2010-09-14
you need to turn on compiz.
run this command in terminal->
```
gconftool-2 --toggle /apps/metacity/general/compositing_manager
```

also use the version from ppa "avant-window-navigator-trunk".
```
ppa:awn-testing/ppa
```

it's faster & more stable.

---

### Post by unfoldedtoast on 2010-09-15
Thank you soooo much for the fix, it was bugging me for hours. Have a great night!!!! (or day, depending where your from)

---

### Post by Rasa1111 on 2010-09-15
also, if compiz hogs your resources, or produces freezes,
you can just use [turn on] the metacity compositing manager,
and leave compiz(visual effects) off.

---

