---
title: "[SOLVED] Grub menu disapeared"
date: 2008-12-09
forum: General Help
---

### Post by abcuser on 2008-12-09
Hi,
on Ubuntu 8.10 when starting PC there is no grub menu selection, just Ubuntu starts by default. I probably set some settings, but don't know which one. How to set back that grub menu selection at boot time. I would like to have "recovery mode" just in case if something goes wrong.
Regrads

---

### Post by kpkeerthi on 2008-12-09
In /boot/grub/menu.lst, change the **timeout** parameter.

See [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto) for detailed instructions

---

### Post by MarblePanther on 2008-12-09
You can install startup-manager from synaptic and use it to configure (with a graphical interface instead of manually editing menu.lst) everything about grub including timeout, colors, showing the menu, kernels shown, etc...


edit:


with startup-manager, just tick the box "show bootloader menu" and set the timeout to something around 3 secs so you can choose quickly enough

---

### Post by abcuser on 2008-12-09
> **kpkeerthi said:**
> In /boot/grub/menu.lst, change the **timeout** parameter.

See [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto) for detailed instructions

Hi,
I have found out that grub menu is displaying "Press <Esc> to display grub menu" - if I press <Esc> then grub menu loads.
Regards

---

### Post by MarblePanther on 2008-12-09
You *can* configure it to display the menu and not the "hit escape" stuff

Just follow my directions if you want that instead

---

### Post by abcuser on 2008-12-09
Hi,
to install from Terminal:
```

sudo apt-get install startupmanager

```

Then use: System | Administratio | StartUp-Manager

Thanks a lot,
Regards

---

