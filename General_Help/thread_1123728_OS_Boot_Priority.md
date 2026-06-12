---
title: "OS Boot Priority"
date: 2009-04-12
forum: General Help
---

### Post by Ciwan on 2009-04-12
Hi Guys

I am dual booting, Ubuntu and XP each on a separate HDD.

How can I make my system load XP if I don't touch anything when Starting the PC ???

Thank You.

---

### Post by benerivo on 2009-04-12
Assuming they are both in the grub / boot options, then you can change the order that the OS's appear in /boot/grub/menu.lst.

---

### Post by drs305 on 2009-04-12
There is a setting in menu.lst that is probably set to "default  0". You can change that setting. 0 is the first "title" found in the bottom menu section, 1 is the second "title" found, etc. So if windows was the fourth "title", you would set it to "default  3" since menu.lst starts counting from 0. Include "title" lines that are empty in the count.

You can also install startup-manager, a gui app that will edit menu.lst for you.
```

sudo apt-get install startupmanager
gksudo startupmanager

```
Set the default OS in the boot options tab.
You can also set the menu timeout, backgrounds, etc from StartUp-Manager.
See the link in my signature line for a StartUp-Manager guide.

---

### Post by Ciwan on 2009-04-12
Thank You Guys :)

Really appreciate the help. :)

---

