---
title: "PrintScreen Xubuntu"
date: 2006-12-05
forum: Desktop Environments
---

### Post by Coolaman on 2006-12-05
Hello, sorry for my poor english but i'm french .

I made a little script for Xubuntu's user who want to take a screenshot with a shortcut keyboard . 

Depend :  Zenity and Scrot ( thanks Wapush ) and Xdialog and Imagemagick (both are not necessary )

For those who are interested it's here :

> 

[Printscreen](http://coolaman.free.fr/Divers/Printscreen.tar.bz2)



Function :

- Full / Partial screenshot with show of the result.
- Express function with the name Screenshot-*time*.png in home 
- save with jpg,png,tiff, ppm or by default png ( if files exist, name will be name_01 or 02 ... )
- Time of pause to take pop up or others ( show the time left )
- Management of transparency
- Language : fr,en,de,it,es ( but made with Voila's translation so perhaps it's not very good)

> Installation :
- sudo apt-get install scrot zenity
- Download the script 
- tar -zxvf Printscreen.tar.bz2 where you want ( for example in ~/.Script )
- sudo chmod +x  Printscreen

- parameters of xfce > keyboard > shortcut > add

By default you cannot assign the key of shortcut directly it is necessary to add a new entry (for example script) 

- - > to add, go to directory where you put your script (at home ~/.Script/Printscreen) and press the selected key of shortcut (for example the printscreen touch)

---

### Post by Coolaman on 2006-12-08
Update of first thread

-  if files exist, name will be name_01 or 02 ... work now
- show the time left when pause

---

### Post by Coolaman on 2007-04-01
Update of first post

- Remove Imagemagick for Scrot ( thanks Wapush )
- Remove Choice of resolution and integrated title screenshot ( is it necessary ? )
- Management of transparency

---

### Post by Degeim on 2007-04-02
Thanks:)

---

### Post by CeruleanRaptor on 2007-05-16
srsly this is awesome. Thanks!

---

### Post by Coolaman on 2007-08-31
- Update because xdialog is not installed by default in Feisty.

- Add an express function

---

### Post by Coolaman on 2007-12-15
Update :

Show the result of the screenshot with display ( if Imagemagick is present )

---

