---
title: "how to install screensavers?"
date: 2009-04-18
forum: General Help
---

### Post by JakeHinojosa on 2009-04-18
i downloaded this lock screen theme: [http://gnome-look.org/content/show.php/NSA++GNOME+Lock+Screen?content=89014](http://gnome-look.org/content/show.php/NSA++GNOME+Lock+Screen?content=89014)

how do i install it?

---

### Post by SkippoGuangiacomo on 2009-04-18
System - system settings - display ...
sorry, i made a mistake, it's not display, you need to go to desktop and then you will have screen saver tab...

---

### Post by JakeHinojosa on 2009-04-18
> **SkippoGuangiacomo said:**
> System - system settings - display ...
sorry, i made a mistake, it's not display, you need to go to desktop and then you will have screen saver tab...

i dont understand..... the thing i need to go is in the admistration part or what?

---

### Post by SkippoGuangiacomo on 2009-04-18
yes! You open the menu where there are the possible choice between applications, favorites, etc. where also the shutdown button is, There you'll find the system settings icon, click on it, and the go to desktop icon... etc

---

### Post by JakeHinojosa on 2009-04-18
> **SkippoGuangiacomo said:**
> yes! You open the menu where there are the possible choice between applications, favorites, etc. where also the shutdown button is, There you'll find the system settings icon, click on it, and the go to desktop icon... etc

2 problems,

1. in the readme thing when i downloaded the theme, it said to press alt + f2 and open gconfig-editor, i tried to open it but it said it could not find it.

2. there is no desktop thing there.

---

### Post by SkippoGuangiacomo on 2009-04-18
> **JakeHinojosa said:**
> 2 problems,

1. in the readme thing when i downloaded the theme, it said to press alt + f2 and open gconfig-editor, i tried to open it but it said it could not find it.
Might be because it is not installed
Try sudo apt-get install gconfig-editor, 
or maybe through sinaptic or something similar 

2. there is no desktop thing there.
Maybe your system is structured differently, is there a display or similar to specify those settings?

---

### Post by hikaricore on 2009-04-18
> Installation:

1. Unpack 1 folder 2 files to /usr/share/gnome-screensaver/
* ( directory nsa-images lock-dialog-nsa.glade lock-dialog-nsa.gtkrc

2. Open gconf-editor (Alt+F2, type '**gconf-editor**' and press enter) change the entry apps/gnome-screensaver/lock_dialog_theme from 'default' to 'nsa'

3. Enjoy!


To enjoy this theme fully I recommend using a picture of your choice of size 96x96 px. You could change your current one by going to System > Preference > About Me and click on the button besides your name.

If you want to get back you old theme you should do step 3 in reverse: replace 'nsa' with 'default'

You should always properly follow instuctions.  It says gconf-editor not gconfig-editor.
It's also worth mentioning that this was probably created for Hardy or Intrepid and may not be fully compatible with Jaunty.

---

### Post by JakeHinojosa on 2009-04-18
> **hikaricore said:**
> You should always properly follow instuctions.  It says gconf-editor not gconfig-editor.
It's also worth mentioning that this was probably created for Hardy or Intrepid and may not be fully compatible with Jaunty.

i did mean gconfig

---

### Post by hikaricore on 2009-04-18
There is no gconfing-editor... it's **gconf-editor**.
Read more carefully, you can't just type whatever you want and expect it to work.

---

