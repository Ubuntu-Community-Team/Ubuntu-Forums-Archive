---
title: "Arabic language support.."
date: 2005-06-26
forum: Desktop Environments
---

### Post by still on 2005-06-26
ijust installed language-pack and langauge-support & the arabic x fonts packages for the arabic language, but i still cant read the names of any files or directories in
konqueror, all ican see is agroup of ( ???????? ) and thats all!!

any help?

---

### Post by SGC on 2005-06-26
Just to be sure, did you do the following?

- installing kde's Arabic language pack ( kde-i18n-ar )
  sudo apt-get install kde-18n-ar

- installing Arabic font (I think it cames with kubuntu):
  sudo apt-get install ttf-arabeyes

- Restart kde (or your computer) after doing the above

---

### Post by still on 2005-06-26
everything was setup properly except the (KDE language pack) so idid installed it, restarted and its the same.. 

i also added the arabic language to the list of supported languages in the KDE control center and i can switch the whole interface to arabic but still cant view the 
arabic folders or files.. neither i can switch to write arabic..

so anything ican do?
thanks in advance..

---

### Post by SGC on 2005-06-26
Try to change konqueror's font to an Arabic font from settings > configure konqueror > Appearances

In the **standard font** field try a font that starts with ae_ (If you install ttf-arabeyes fonts) such as "ae_Arab" or "ae_Cortoba" and hit apply. This should change the folders names from ?????? to thier real name. Try to create a new folder or file with arabic name just to be sure.

Also try to change the default encoding from, settings > configure konqueror > fonts, and change the encoding to **utf8** from the **defualt encoding** drop-down menu 

As for switching to Arabic, KDE's keyboard layouts is not perfect , So Open /etc/X11/xorg.conf

And betwen **Section "InputDevice"** and **EndSection** enter the following to switch between Arabic and English using ALT-SHIFT:
```

Option  "XkbLayout" "us,ar"
Option  "XkbOptions" "grp:alt_shift_toggle,grp_led:scroll"

```

You need to disable kde's keyboard layout from:
Control centrer -> Regional & Accessibility > Keyboard Layout
uncheck **Enable keyboard layout** from **layout** tab and uncheck **Enable xkb options** from **Xkb Options** tab. Hit apply then restart your computer.

I hope that helps.

---

### Post by still on 2005-06-27
really thanks for ur help & patience SGC.

well, idid changed the standard font to ae_arab and still the folder & files have the
??????? names, changed the encoding (although idont think it has something to do with file browsing as this section is related to web browsing) but still has no effect..

configured the input layout section in xorg.conf file and i can creat new files or folders in arabic properly but still cant see the already existing ones,,

although the problem isnt solved yet but am really surprised why it doesnt view em 
properly albeit ican creat new files/folders in arabic!! 

anything has todo with fonts? imean mayb the font in which its already created isnt supported/installed in kubuntu?? naive thinking iknow but this s real weired!

thanks again..

---

### Post by SGC on 2005-06-27
Did you try to reanme those files/folders with ???????? , are they created in windows or kubuntu?

And yeah the fonts encoding was for web browsering, not for the file managment mode. I didn't relize that.

---

### Post by still on 2005-06-27
yes renaming those files/folders is possible and ican see thier arabic names properly after renaming. 
they've been created originally in windows icant see a prob. in this..but iguess we almost solved the prob. so far, but its still weired that kubuntu cant auto. recognize
those files/folders already created with other languages! but heey welcome to the 
linux world!!  ;-) 

really thanks man for ur great help..

---

