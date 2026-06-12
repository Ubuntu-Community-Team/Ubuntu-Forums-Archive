---
title: "icon packs not installing correctly with theme"
date: 2009-05-10
forum: General Help
---

### Post by skeetworthy on 2009-05-10
I've downloaded a few themes and installed them but when I use them I get an error on all of them saying this theme will not look as intended because the required icon theme is not installed.  What am I doing wrong?

---

### Post by skeetworthy on 2009-05-11
Is anyone going to help me with this???

---

### Post by VCoolio on 2009-05-11
A theme is placed in ~/.themes and usually only comes with gtk2 (the controls) and metacity (window borders). The icons that the author intends to go with it have been indicated, so that the theme complains when they are not found, but you have to install them yourself in ~/.icons. Probably to be found on gnome-look.org. In the meanwhile the theme will work fine, and you can choose whatever icon theme you like to go with it. If you want to get rid of the message modify the icon theme mentioned in the file in ~/.themes/yourtheme/index.theme.

---

### Post by skeetworthy on 2009-05-11
Ok for some reason I thought that the icon pack was included and It was'nt installing for some reason.  I downloaded hydroxygen which is the icon pack it said I needed for it to look like it is suppost to.  Now I get an error when im trying to extract the files which reads "unzip:  cannot find or open /tmp/hydroxygen_iconset_by_deviantdark.zip, /tmp/hydroxygen_iconset_by_deviantdark.zip.zip or /tmp/hydroxygen_iconset_by_deviantdark.zip.ZIP." Thank you for your help so far.

---

