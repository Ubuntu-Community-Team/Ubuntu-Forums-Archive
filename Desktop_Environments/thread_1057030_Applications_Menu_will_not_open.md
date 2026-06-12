---
title: "Applications Menu will not open"
date: 2009-02-01
forum: Desktop Environments
---

### Post by icrywolf on 2009-02-01
Applications Menu will not open from the top bar, but Places and System menu's do, Using Intrepid Ibex Ubuntu, 

I have no idea on how to open it again - I already tried adding another gnome menu bar but it has the same effect

help?

---

### Post by gettinoriginal on 2009-02-01
Have you tried rebooting ??  If you have and it didn't work, try this:
Reboot > during grub splash, hit escape > Recovery mode > Enter (let finish)
Repair Broken Packages > Enter (if it asks about updates hit N) (let finish)
Try to fix X server > Enter (Let finish)
Resume normal Boot > Enter

---

### Post by icrywolf on 2009-02-01
Tried what you said, but still hasn't worked :(

---

### Post by imdfuture9999 on 2009-02-03
evn i have the same problem....... donno how to fix .. it was al workin fine for over a month now.. bt y did it happen . i guess its due to the last auto-updates i did.. it doest evn show up to edit the menu bar. Applications tab dosent open but places & system is totaly functional. find out the sol,,,,soon...

---

### Post by imdfuture9999 on 2009-02-03
and by trying to fix the Xserver 7 etc as u said in the above post did not work out 4 me.. but i lost my graphics nd its not loading my nvidia drivers now.. nd my appearance goes to none. cnt get wats wrong in there..

---

### Post by icrywolf on 2009-02-05
**Ok I found a solution :D Type this into the Terminal:**

```
rm ~/.config/menus/applications.menu
```
**I found this information from this website, it should work for Hardy Heron and Intrepid Ibex:**
[http://blog.jelthure.com/ubuntu/ubuntu-710-gutsy-gibbon-applications-menu-wont-open/](http://blog.jelthure.com/ubuntu/ubuntu-710-gutsy-gibbon-applications-menu-wont-open/)

---

