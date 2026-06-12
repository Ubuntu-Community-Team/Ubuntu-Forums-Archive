---
title: "Main Menu Ubuntu Icon and Beryl (new version) tray Icon...how do I change them?"
date: 2007-01-30
forum: Desktop Environments
---

### Post by mrdeeno on 2007-01-30
I have been trying to figure out how to change these 2 icons forever.

I am running Edgy with the new version of beryl, and I have my lower panel sized small and it cuts the top of the beryl icon off.  

And I have the main menu (the one without text) in my upper panel and want to change the ubuntu logo icon to soemthing else.  

Anyone know?

---

### Post by BarfBag on 2007-01-30
/usr/share/icons/hicolor/scalable/apps/beryl-manager.svg

That's the location of the Beryl icon.  Just replace it with the one you like and restart GNOME.

Not sure about the Ubuntu icon.

Edit - the Ubuntu icon is located at /usr/share/icons/Human/scalable/places/gnome-main-menu.svg.  Do the same thing.

---

### Post by ComplexNumber on 2007-01-30
if the theme doesn't have the gnome-main-menu icon, then it will use that of the icon theme that it 'inherits'(ie if a theme doesn't contain all the relevant icons that it needs to show, it will use the icons of the theme that it inherits). if you have a look in the index.theme file in the icon theme, it often states what icon theme it inherits. and if the inherited theme (if stated) doesn't have all the necessary icons, then  it will just use icons in the  gnome theme then the hicolor theme to make up the shortfall. hope that makes sense. 

so if you want to change the main menu botton from being the ubuntu icon to something else, change the following icon:
/usr/share/icons/gnome/scalable/places/start-here.svg

---

### Post by mrdeeno on 2007-01-30
Excellent!

it worked, thanks all

---

### Post by K.Mandla on 2007-01-30
(Moved to Desktop Environments. ;) )

---

