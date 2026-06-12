---
title: "About Customizing livecd"
date: 2009-04-07
forum: General Help
---

### Post by fprg on 2009-04-07
Hi,I want to customize a new Desktop livecd just for Chinese. There's 3 problems below:

1.I think that we need not select language/city/keyboard during installation. How to remove the steps and just give a default setting? 

2. Apt-testing waste much time. How to remove the step?

3.I set the system in chroot environment. I find that the file /etc/apt/sources.list will be overwrite after installation.

  I use the command below. I find it not take effect after installation:
  > gconftool-2 --type bool --set /apps/nautilus/desktop/computer_icon_visible True

  I also use the next command belose. It take effect.

  > conftool-2 -t bool --set /apps/gedit-2/preferences/editor/save/create_backup_copy False
   
  I don't know what's wrong.   

Can anyone help me? Thank you.

---

### Post by fprg on 2009-04-07
Is there someone can help me?

---

### Post by fprg on 2009-04-07
I solve the third problem by myself.

>  gconftool-2 --direct --configsource xml:readwriter:/etc/gconf/gcconf.xml.default --type bool --set /apps/nautilus/desktop/computer_icon_visible true

---

