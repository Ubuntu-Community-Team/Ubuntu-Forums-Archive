---
title: "Screen goes black"
date: 2009-02-06
forum: Desktop Environments
---

### Post by kuriozux on 2009-02-06
Hi All,

My Ubuntu has been working great, but today I restarted it and got some flaky black windows, and each time I click on desktop the area becomes black.

I can't see anything when I click the menu as the drop down is also black with some flaky rainbow color.

Can anyone help?

Thank you in advance

---

### Post by gettinoriginal on 2009-02-07
Try ctrl/alt/backspace, that should kill x and then log in and see if it works.

---

### Post by kuriozux on 2009-02-07
> **gettinoriginal said:**
> Try ctrl/alt/backspace, that should kill x and then log in and see if it works.

Thanks for responding, but that didnt work.

Anything else that could fix this?

---

### Post by gettinoriginal on 2009-02-07
System Restore
Reboot > during grub splash, hit escape > Recovery mode > Enter (let finish)
Repair Broken Packages > Enter (if it asks about updates hit N) (let finish)
Try to fix X server > Enter (Let finish)
Resume normal Boot > Enter

---

### Post by kuriozux on 2009-02-07
All those steps were successful, but it's still doing the same thing.

Is there anything I can do using the live cd?

---

### Post by gettinoriginal on 2009-02-07
Go to System, Administration, Hardware Driver, deselect the driver, reboot, then go back to Hardware Driver and select it.

---

### Post by kuriozux on 2009-02-07
> **gettinoriginal said:**
> Go to System, Administration, Hardware Driver, deselect the driver, reboot, then go back to Hardware Driver and select it.

The sad part is that I cant even go to anything because I cant see any of the menus.

I also noticed that updating pkg said it cannot be found or cannot connect. dont know whats happening there.

---

