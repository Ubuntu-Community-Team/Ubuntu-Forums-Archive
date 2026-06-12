---
title: "Default theme?"
date: 2009-08-03
forum: Desktop Environments
---

### Post by b3n0 on 2009-08-03
Hey all,

I was wondering if there is a quick way to restore the Ubuntu 9.04 default theme? After playing around with a few tutorials, and making my desktop look like Mac OS X; I've gotten board and I'd like to return to the default theme. I'm sick of having the 'X', minimise, and maximise buttons on the left, how do I change the position of these buttons back to the right? Also, I've lost my tool bar down the bottom. How do I get that back?

Thanks for your help.

---

### Post by wojox on 2009-08-03
To get a new panel Right click a panel and choose add new panel. As far as your theme, if you go to System > Preferences > Appearance you can choose a new theme. If you Customised your default theme you may have to go to Gnome and download a new one.

---

### Post by YolaGP on 2009-08-03
The default theme is **human**. (System>preferences>appeareance>theme tab) Your buttons will be on the right side.
To create the lower panel, right click in the existing panel>add new panel. Drag the new panel down if necessary.

---

### Post by b3n0 on 2009-08-03
I changed the themes a few times, however I'm still sporting a very Mac-esque Left hand exit, minimise, and maximise button group.[URL="http://maketecheasier.com/turn-your-ubuntu-hardy-to-mac-osx-leopard/2008/07/23"]
This is the tutorial I followed.[/URL]

---

### Post by pmlxuser on 2009-08-03
delete .gnome2 folder in your home folder. it also helps to delete .gnome2_private

i.e 
```

$ cd ~
$rm -r .gnome*

```

all gnome setting that you had will go leaving you with the default setting that you get on a fresh install. you have to recreat all short cuts and the like.

---

### Post by Fzang on 2009-08-03
To change the position of buttons, run gconf-editor and go to 

apps > metacity > general, and change button_layout to menu:minimize,maximize,close

---

### Post by b3n0 on 2009-08-04
> **Fzang said:**
> To change the position of buttons, run gconf-editor and go to 

apps > metacity > general, and change button_layout to menu:minimize,maximize,close

Fantastic! That works well!

---

