---
title: "Help installing themes"
date: 2008-03-31
forum: Desktop Effects &amp; Customization
---

### Post by bundleboy on 2008-03-31
Hi i am new to Ubuntu, i am on Gutsy 7.10 i have CompizConfig installed and i am clueless on how to install themes... i tried dling from gnomelook and other theme websites but however they come with the extension .emerald and i dont know how to go about installing the themes any help will be appreciated thanks

Karthik

---

### Post by gavintlgold on 2008-03-31
By default, the emerald window decorator is not installed. You may be using the gtk-window-decorator as a decorator.

Make sure you have the programs "emerald" and "emerald-themes" installed, then you should be able to find the "emerald themer" in your menus and add a theme with "import...".

Also make sure you are starting compiz fusion with emerald and not the gtk-window-decorator.. you might need to make a startup item > "emerald --replace" if it doesn't work.

---

### Post by bundleboy on 2008-03-31
hi i tried searching for emerald themes and i was brought to beryl project but isnt beryl replaced with compiz on 7.10? if so how do i install emerald themes or gtk-window-decorator? and is there a repos where i can get emerald theme from? 
thanks much

---

### Post by gavintlgold on 2008-03-31
The files ending in .emerald are correct. Emerald is the window decorator, and worked in Beryl and not compiz originally. This is why you are seeing references to Beryl and not compiz fusion.

Compiz fusion, however, supports .emerald theme files. Don't worry, any .emerald themes will work with compiz fusion if you've installed emerald.

---

### Post by bundleboy on 2008-03-31
hi thanks for the reply i have managed to installed emerald and i can do ```
emerald --replace
``` however my panels do not change like the samples shown do u know how i can make the panels change aswell i am using [http://www.gnome-look.org/content/show.php/Dark+Ice+Emerald?content=70284](http://www.gnome-look.org/content/show.php/Dark+Ice+Emerald?content=70284) that theme..
thanks

---

### Post by Helios1276 on 2008-04-01
Hey man, don't know if this will help but have you got your custom theme select in System-Preferences-Appearance? That command should work fine to get the panels up as long as you have the theme you downloaded imported into emerald.

---

### Post by Helios1276 on 2008-04-01
Ah wait hang on, ignore my last post. I have no idea how you do that or if it's possible lol I just played with panel transparency to suit my 'glassy' desktop style

---

### Post by bundleboy on 2008-04-02
hey hi thanks for the tip but i have manage to install the Mac-Like panel from help at compiz forums.. its just that i did not know what to look for but gavintlgold gave me tips on what to search for so i manage to do it :D thanks man

---

