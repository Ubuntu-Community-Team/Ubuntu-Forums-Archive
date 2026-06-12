---
title: "Fusion-icon SVG link image not found"
date: 2007-10-15
forum: Desktop Effects &amp; Customization
---

### Post by shakaran on 2007-10-15
I have Ubuntu Gutsty and i install fusion-icon, but icon is dead.

/usr/share/icons/hicolor/scalable/apps/fusion-icon.svg

It is empty!!

Because, the path of image is wrong (attach image).

(And my username not is scott XD. Maybe a developer?)

---

### Post by shakaran on 2007-10-21
Hey, no anwsers?

---

### Post by itsjustarumour on 2007-11-17
> **shakaran said:**
> I have Ubuntu Gutsty and i install fusion-icon, but icon is dead.

/usr/share/icons/hicolor/scalable/apps/fusion-icon.svg

It is empty!!

Because, the path of image is wrong (attach image).

(And my username not is scott XD. Maybe a developer?)

Hmmm...I just spotted the same thing...

---

### Post by shakaran on 2007-11-17
I try to solve this problem. I look icons in google and I put icons on these paths:

/usr/share/icons/hicolor/22x22/apps/fusion-icon.png
/usr/share/icons/hicolor/24x24/apps/fusion-icon.png
/usr/share/icons/hicolor/32x32/apps/fusion-icon.png
/usr/share/icons/hicolor/48x48/apps/fusion-icon.png
/usr/share/icons/hicolor/scalable/apps/fusion-icon.svg

The files are attached in the post. 

The developers should solve this problem FAST. Meanwhile, maybe this is a possible solution.

---

### Post by VON_CAPO on 2008-01-13
> **shakaran said:**
> I try to solve this problem. I look icons in google and I put icons on these paths:

/usr/share/icons/hicolor/22x22/apps/fusion-icon.png
/usr/share/icons/hicolor/24x24/apps/fusion-icon.png
/usr/share/icons/hicolor/32x32/apps/fusion-icon.png
/usr/share/icons/hicolor/48x48/apps/fusion-icon.png
/usr/share/icons/hicolor/scalable/apps/fusion-icon.svg

The files are attached in the post. 

The developers should solve this problem FAST. Meanwhile, maybe this is a possible solution.
Thanks :)

---

### Post by shakaran on 2008-01-13
There's no way around that.

---

### Post by glennric on 2008-01-13
How are you installing fusion-icon?  I installed it from the git repository and the icons are there.

---

### Post by VON_CAPO on 2008-01-13
I installed using the package " fusion-icon_1.0-1.0_i386.deb ".

Also, this package has the problem that the original icon is not visible on a panel with less than 26 pixels.

But replacing the icons with the file uploaded for **shakaran** (hicolor.tar.gz) , the icon is again visible with a default size of 24 pixels.

---

### Post by glennric on 2008-01-13
> **VON_CAPO said:**
> I installed using the package " fusion-icon_1.0-1.0_i386.deb ".

Also, this package has the problem that the original icon is not visible on a panel with less than 26 pixels.

But replacing the icons with the file uploaded for **shakaran** (hicolor.tar.gz) , the icon is again visible with a default size of 24 pixels.

Where did you get that deb?  The problem it seems is not the developers that make fusion-icon, but whoever it was that made the debian package you are installing with.

Try installing with the deb I attached.

---

### Post by VON_CAPO on 2008-01-13
> **glennric said:**
> Where did you get that deb?  The problem it seems is not the developers that make fusion-icon, but whoever it was that made the debian package you are installing with.
Here: ---> [http://ubuntuforums.org/showpost.php?p=3163821&postcount=8](http://ubuntuforums.org/showpost.php?p=3163821&postcount=8)

---

### Post by glennric on 2008-01-13
Let me know if that deb works or not.

Edit:  That is the deb I posted two posts back.

---

### Post by VON_CAPO on 2008-01-13
I uninstalled the old package, then I restarted X and I installed your package.

Your package looks identical to the old one but with the new blue icon (the old one had a red and black icon).

Also your package has a fundamental advantage:
To switch from Compiz to Metacity = 0,3 seconds (the old one= 1.5 second)
To switch from Metacity to Compiz = 1.5 second (the old one almost 3 seconds)

Thanks a lot. :popcorn:

---

