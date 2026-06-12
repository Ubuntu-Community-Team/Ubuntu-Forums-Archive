---
title: "Colour Scheme"
date: 2006-08-15
forum: Desktop Environments
---

### Post by niteblind on 2006-08-15
Hi,

Can anyone shed some light on this for me. I am trying to sking my ubuntu to look like my windows machines do. this is what I am trying to get to [http://www.niteblind.net/pictures/theme.JPG](http://www.niteblind.net/pictures/theme.JPG)

I know people will not like the scheme but I am visually impaired and cant yse anything else. I am currently running the inverse high contrast theme that comes with gnome but i personally dont like it and would rather get to the above in stead.

I tried going into the following directory /usr/share/themes/HighContrastInverse/gtk-2.0 and editing the gksrc file but it does not seem to make any difference when i restart the changes have made no affect can anyone let me know why? As below I changed the hex value for the PanelMenu stripe-gradient-top line to #FFFFFF and it still is set to the same as before.

style "default"   
{ 
  engine "hcengine" {}	

# For Java Desktop System
  PanelMenu::stripe-gradient-top = "#FFFFFF"
  PanelMenu::stripe-gradient-bottom = "#000033"
 

Am I at least on the right track ie modify the values in the already existing file to match what i want to get?

Also along the same lines if I install any kde programs they obviously dont get affected bu the colour schemes is there any way to skin them from GNOME?

cheers for any assistance in advance.

niteblind

---

### Post by niteblind on 2006-08-15
why is this such a mystery surely someone must know the answer to these quetions? is there a howto I have missed?

niteblind

---

