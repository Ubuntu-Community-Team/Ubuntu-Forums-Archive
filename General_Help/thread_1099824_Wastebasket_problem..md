---
title: "Wastebasket problem."
date: 2009-03-18
forum: General Help
---

### Post by ekidd91 on 2009-03-18
OK, so I've looked around and haven't found a solution for my problem. The problem is that when I hover over my wastebasket it says there are '5 Items in the Deleted Items folder' and yet when I open it it is empty and no matter how many times I click empty it still tells me there's five items and the icon show a full wastebasket rather than an empty one.

Any ideas?

Screenshot attached.

Thanks.

---

### Post by LowSky on 2009-03-18
Are you sure there are no hidden files?

Ctrl+H will allow you to see hidden files and folders

also log inst Nautilus as root to see if stuff shows up in the trash

 presss Alt +F2 and type gksu nautilus

---

### Post by ekidd91 on 2009-03-18
OK, I've tried those suggestions and neither has shown any files.

I think the problem is with the wastebasket icon on the taskbar: it never changes, whereas the icon within Nautilus does change. Within Nautilus I'm unable to select 'Empty Deleted Items' but I am able to if I rightclick on the icon in the bottom right.

---

### Post by markharding557 on 2009-03-18
i had this problem before and dealt with it by opening nautilus as root in a terminal
> gksu nautilus
and deleting the files there

---

### Post by ekidd91 on 2009-03-18
> **markharding557 said:**
> i had this problem before and dealt with it by opening nautilus as root in a terminal

and deleting the files there

Just tried this, upon clicking on Deleted Items i get an error message reading "The folder contains contents which could not be dislayed. Sorry, could not display all the contents of "trash": operation not supported"

---

