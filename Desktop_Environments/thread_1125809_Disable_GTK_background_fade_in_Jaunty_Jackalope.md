---
title: "Disable GTK background fade in Jaunty Jackalope"
date: 2009-04-14
forum: Desktop Environments
---

### Post by markoid8 on 2009-04-14
I upgraded to the Jaunty Jackalope beta a few days ago, and I have been experiencing performance problems with the new feature. I have wallpapertray, a small panel app that changes my background periodically, and my integrated graphics [chipset] is not designed to handle that kind of animation, and it maxes out my CPU for a few seconds every minute. I **really** want to diasble this feature, but I cannot find a reference in gconf-editor, or Compiz. Another thread said that it was a GTK feature.

**Does anyone know how to disable this feature?**

Thanks in advance.

---

### Post by eaidoido on 2009-04-29
bump. i'd also like to.

---

### Post by kanikilu on 2009-04-29
[http://ubuntuforums.org/showpost.php?p=6900489&postcount=16](http://ubuntuforums.org/showpost.php?p=6900489&postcount=16)

---

### Post by ashkool on 2009-06-08
> **kanikilu said:**
> [http://ubuntuforums.org/showpost.php?p=6900489&postcount=16](http://ubuntuforums.org/showpost.php?p=6900489&postcount=16)

That works! Thank you :D

---

### Post by rvoro on 2009-07-05
A partial solution for metacity users is to make metacity a composing manager. 

Run the "gconf-editor" command.
Go to apps-> metacity -> general.
Check the "composing_manager" option.

In my case, the result of this was that, although performance-wise I still experienced the same CPU spikes and temporary interface freezes while changing desktop images, visually there was no longer the "fade" effect during the transition between pictures. Instead, pictures changed directly from one to the other, as they did previously in Gnome (though now with a slight delay).

---

### Post by rvoro on 2009-09-06
For those of you with Intel graphics chipset, the solution should come with the next release of Ubuntu (9.10 karmic koala). Currently the solution is listed as unstable, but I tried it and it worked for me! :D
The link below provides the solution (really simple), as well as guide to what to do if something goes wrong (which seems simple as well).
[https://wiki.ubuntu.com/X/UxaTesting]("https://wiki.ubuntu.com/X/UxaTesting")

---

