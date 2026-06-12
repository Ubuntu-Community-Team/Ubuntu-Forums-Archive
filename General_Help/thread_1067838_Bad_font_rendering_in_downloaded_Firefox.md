---
title: "Bad font rendering in downloaded Firefox"
date: 2009-02-12
forum: General Help
---

### Post by enli on 2009-02-12
Hi,

I have the latest firefox installed from the synaptic and I have around 10 add-ons installed in it. The problem is, in customize toolbar these addons are not present. 

So the other day I downloaded firefox from official site which comes in .tar.gz format. It runs and all my addon buttons are displayed correctly in the "customize toolbar" but the fonts are rendered very badly just like when cleartype is not enabled on Windows machines.

I tried to get screenshots but that effect cant be seen in pictures, but I can feel it. The firefox from the synaptic renders the font correctly. Does anybody know how to correct either of these problems?

-EnLi

---

### Post by mixmaster on 2009-02-12
I had some very peculiar font issues in Firefox which were cured by clearing the cache and restarting.

---

### Post by spcwingo on 2009-02-12
Do you have msttcorefonts installed?  That might help your problem.  Alternately, you can create a folder named .fonts (or .font, I can't remember) and place you font of choice in that folder.  To enable that font just open Firefox and go to edit>preferences>content>default font.  Select your font and you're in business.  :D

---

### Post by enli on 2009-02-12
Clearing the Cache didnt help.

I use "Lucida Grande" for firefox from synaptic and it works there .

I changed to other fonts such as "Arial" but still fonts are not rendered correctly. Thats very annoying !

EDIT : I removed the old firefox config from ~/.mozilla/firefox . Reinstalled firefox and all is good now ;)

Hope it helps somebody having the same problem.

---

