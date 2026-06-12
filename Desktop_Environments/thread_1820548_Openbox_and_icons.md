---
title: "Openbox and icons"
date: 2011-08-07
forum: Desktop Environments
---

### Post by whatthefunk on 2011-08-07
I've been trying to change some of the icons in my system.  I first tried the GUI.  This changed the icon in the start menu, on the panel, and on the desktop, but it doesnt change the icon in the left-hand corner of open windows or in the task bar in the panel.  I then went in and did it manually by editing the .desktop files in /usr/share/applications.  Same thing...the icons in Openbox windows are the old ones.  My guess is that Openbox is looking elsewhere for icons, but I dont really know.  Does anybody have an idea?

---

### Post by kerry_s on 2011-08-07
see pic, is that the 1 ?

i don't use them myself, i just remove the "N".

---

### Post by whatthefunk on 2011-08-07
> **kerry_s said:**
> see pic, is that the 1 ?

i don't use them myself, i just remove the "N".

Thats the one.  Where do you remove the N from?

---

### Post by kerry_s on 2011-08-07
Preferences-> customize look & feel
Or
Preferences-> openbox configuration manager

Look under the window setting.

here's a late pic, i was in the bathroom when i responded.

---

### Post by whatthefunk on 2011-08-08
Thats one option.  I would really like to know where Openbox is reading its data about the applications that it launches.  Not only are the icons different, but Ive noticed that some menu items have different names in the menu and in the window suggesting that the menu and Openbox are reading different files.  I cant seem to find an answer anywhere though...

---

### Post by kerry_s on 2011-08-08
I think it uses mime files + the theme icons. 
I have no idea how it works though.

---

### Post by whatthefunk on 2011-08-08
I think it does this for system icons, but I cant find anything in my gtk files mentioning applications like firefox.  This is driving me nuts...

---

### Post by kerry_s on 2011-08-08
It would be deeper than gtk, it would be in code itself.

---

### Post by whatthefunk on 2011-08-08
Got a work around.  Most programs store icon files in /usr/share/pixmaps.  To change the icon in the window bar, all you have to do is copy your new icon to this folder and rename it to whatever the old icon was called.  So if you wanted to change the firefox icon permanently to be a picture of your dog or something, you copy that picture into pixmaps and call it "firefox."  Messy, but it works.  Good bye ugly icons!

---

