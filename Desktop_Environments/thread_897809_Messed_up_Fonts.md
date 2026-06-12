---
title: "Messed up Fonts"
date: 2008-08-22
forum: Desktop Environments
---

### Post by afderrick on 2008-08-22
Alright I'm having some problems with the arial font when opening up documents in OpenOffice.  My "arial" font is all messed up.  I know there can't be much wrong with this since I looked in my /usr/share/fonts folder and found the arial font located in that folder and it looked normal on the preview.  So I'm wondering if anyone else has had this problem and what I might be able to do to solve it?  

I would think there has to be another font located somewhere under the same name that is being scanned before the folder with the correct arial font, right?

---

### Post by silkstone on 2008-08-22
If there is no other font of the same name in that folder, look in ~/.fonts and see if anything is there. (You may not have that folder if you haven't installed fonts manually.)

My only other suggestion is to uninstall and reinstall msttcorefonts and see if that cures it.

---

### Post by afderrick on 2008-08-22
There is a .fonts folder but it's empty.  I completely removed msttcorefonts package and reinstalled, still getting a funny looking arial font, almost like OO is pointing Arial to the wrong font and calling it arial.

---

### Post by coffeecat on 2008-08-22
After you've made sure that there is no duplicate Arial ttf file in ~/.fonts, try regenerating the font cache. Open a terminal and:

```
sudo fc-cache -fv
```

---

### Post by afderrick on 2008-08-22
Still nothing, but I did receive several errors for invalid cache files in ~/.fontconfig folder.  Arial font is still messed up though, I might have to perpetually resign to the verdana font.

---

### Post by Cheesehead on 2008-08-22
Does this occur *only* in Openoffice?
Can you reproduce it in AbiWord or Inkscape or any other font-using apps?

---

### Post by afderrick on 2008-08-22
Okay, I appreciate the help there, didn't think about that.  It is just the OpenOffice that has arial messed up, so it might be pointing at the wrong font or loading them incorrectly?

---

### Post by coffeecat on 2008-08-22
If it's just Open Office that you're having the font problem in, you might find [The Open Office forum]("http://user.services.openoffice.org/en/forum/") helpful.

To be honest, I've never used it, but it looks fairly lively and it has a Linux subforum in the troubleshooting section.

---

