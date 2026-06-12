---
title: "Fedora 8 Help?"
date: 2008-02-03
forum: Fedora/RedHat and derivatives
---

### Post by koldphlame on 2008-02-03
Help with installing [[COLOR="Yellow"]B]_[COLOR="Red"]FLASH[/COLOR]_[/B][/COLOR]

---

### Post by zorkerz on 2008-02-03
Im not quite sure what your looking for here. If your trying to install flash in Fedora 8 I would imagine that the best help would come from fedora centered forums. Please be a bit more specific both with your post title (so people who can help find you) and with describing your problem.
good luck

---

### Post by igknighted on 2008-02-04
This is actually even better than with ubuntu.  You have three options:

1) Download the plugin itself from adobe.com (in .tgz form) and run the install script provided.

2) Download the flash .rpm file, double click it (or let firefox just open it with software installer) and type the root password.

3) Download the adobe YUM repo rpm.  To do this, choose the third option on the adobe page.  Install the rpm as above, but instead of installing the player, it installed an adobe-maintained repo.  Now use YUM to install the plugin with "yum install flash-plugin", or through Yumex/Pirut.

#3 is the preferred method, as it will let the package manager update it should you choose every time a new version is released.

Link: [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&promoid=BONRN](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&promoid=BONRN)

---

### Post by justin whitaker on 2008-02-04
One of the first things you want to do with Fedora is tell YUM that there is this repository called Livna, and it should check it out for software. All the proprietary media stuff that can't be shipped on Fedora proper is there....sort of like Medibuntu.


Edit:

Nevermind, flash isn't in the repo. igknighted has it right.

---

### Post by whitefang5412 on 2008-02-05
Usually flash doesn't install or work until you get done with all the udpates. If you haven't installed the updates, or chose to recieve them you need to fix something here....

---

