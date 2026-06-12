---
title: "Printing option missing from Admin menu"
date: 2007-01-07
forum: Desktop Environments
---

### Post by kbudurka on 2007-01-07
Hi all,

I am running 6.06 and today I noticed that I can no longer print to a printer on my son's Windows XP PC. I thought, ok, something might have gotten changed or hosed, I will just reinstall the printer.

However now I notice that my System > Administration > Printing icon/option is gone.
I tried reloading cups, but still nothing.

I've search and I can not find anyone who had this issue. Any ideas how to get my icon back so I can begin to troubleshoot my printing issue?

Thanks!

---

### Post by jpeddicord on 2007-01-07
Try this:
Right-click on the menubar, and go to Edit Menus. From there, find the Administration category under System. There should be a printing item there; check the checkbox to reactivate it on the menu.

Hope that helps! :KS

---

### Post by kbudurka on 2007-01-07
Thank you for the suggestion.

I tried this and there is no Printing option in that Applications window. It's like the tool is simply "gone".

I wonder if there is a cmd line equivalent? Or something I can try to reinstall?

---

### Post by jpeddicord on 2007-01-09
Press Alt+F2 and type `gnome-cups-manager` to start the Printing manager. You may also type it into the terminal if you wish.

You can also try adding it to the menu from the Edit Menus dialog. Just type in gnome-cups-manager for the Command field, and give it a name.

---

### Post by kbudurka on 2007-01-09
Thank You!

I tried running gnome-cups-manager, but it wasn't found.
I did an apt-get install gnome-cups-manager and it installed.
My printer icon is back!

Whew....

---

