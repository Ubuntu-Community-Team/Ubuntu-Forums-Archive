---
title: "[ubuntu][opera] opera icons on panel"
date: 2011-12-12
forum: Desktop Environments
---

### Post by tr4rex on 2011-12-12
ubuntu 10.04, gnome 2.30.2, opera 11.6
how to repear normal opera icon on top panel?
[http://imageshack.us/photo/my-images/703/screenshotjir.png/](http://imageshack.us/photo/my-images/703/screenshotjir.png/)

---

### Post by Frogs Hair on 2011-12-12
Hello and Welcome 

Close Opera  ,  reset the panel to defaults with the following command  , and check for any change .  
```
gconftool --recursive-unset /apps/panel && killall gnome-panel 
```

---

### Post by tr4rex on 2011-12-13
no, these bug hasn't dissappeared.

---

### Post by Frogs Hair on 2011-12-13
I thought it may be an error in the panel . I am an Opera user and haven't  seen this before . This is a bit extreme , but You could reinstall  Opera . Export your bookmarks to a folder first then use Crtl +H in the home folder to locate and delete the .opera folder . If the problem is caused by the configuration it will be removed with the folder and a new one will be created when you install .

---

### Post by tr4rex on 2011-12-13
small addition to my topic: as far as I remember it's appeared after upgrading opera from 11.52 up to 11.6

---

### Post by Frogs Hair on 2011-12-13
That leads me to think the configuration folder is corrupt. There are many items in the .opera folder , so it may be easiest to delete the folder and reinstall as I suggested rather than trying to figure out which item or file is causing the problem . The Opera forum is another resource to check also.

---

