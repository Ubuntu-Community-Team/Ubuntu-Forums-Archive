---
title: "Ubuntulooks"
date: 2009-02-13
forum: General Help
---

### Post by XtrackterX on 2009-02-13
I am new to this forum, and I wnat to install a theme but on the Appearance it says GTK + Theme Engine "UbuntuLooks" Is not installed.

I downloaded it and read the readme
On Step #1:
Copy libubuntulooks.so and libubuntulooks.la to /usr/lib/gtk-2.0/2.*.*/engines as root (substitute "2.*.*" with your version number)

I am running Ubuntu 8.10

It won't let me copy, it Permission Denied.
Do you know how to fix it?
If you do, thanks in return.
-RJ

---

### Post by jenkinbr on 2009-02-13
You need to use sudo to copy files as root.

```
sudo cp ./libubuntulooks.so ./libubuntulooks.la /usr/lib/gtk-2.*.*/engines/
```

Again, make sure you replace 2.*.* with the proper version number.

---

### Post by XtrackterX on 2009-02-13
Is there any other way to do this?

---

### Post by oldos2er on 2009-02-13
> **XtrackterX said:**
> Is there any other way to do this?

 Open a terminal, and enter
```
sudo aptitude update && sudo aptitude install gtk2-engines-ubuntulooks
```

---

### Post by fragos on 2009-02-14
In general you can open a root nautilus window by doing Alt-F2 and running "gksudo nautilus". In that window locate the destination. Now open natilus as the user and navigate to the source folder. You'll now be able to move or copy from the user folder to the root folder. I recommend you change the background for nautilus in the root window so it will always be visualy obvious that you have a root window open. Clicking a file in the root window will open that file with root permisions. Handy for editing configuration files in /etc. I also set a different theme for gedit as root to help me keep track of what I'm doing.

---

