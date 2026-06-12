---
title: "Lubuntu 14.04 Desktop ignores English(UK) and uses English(US) in keyboard and locale"
date: 2014-07-28
forum: Desktop Environments
---

### Post by BrianJB on 2014-07-28
My desktop displays the locale as US and provides a US keyboard, ignoring the correct UK default settings.
This is my default locale in /etc/default/locale
LANG="en_GB.UTF-8"
LANGUAGE="en_GB:en"

and this is /etc/default/keyboard
XKBMODEL="pc105"
XKBLAYOUT="gb"
XKBVARIANT=""
XKBOPTIONS=""

Settings Preferences/languagesupport are als ignored 
Settings Preferences/input device preference/keyboard is UK and tests correctly with a UK keyboard. This email give correct GB £ from my keyboard, but a console reverts to US keyboard output, printing £ as $.

I just had to restart the PC. After the restart I can only get the keyboard to output US symbols.

Can anyone help with these problems?

I've just solved it myself. The keyboard layout handler does not recognise defaults on installation. In adition it does not display the correct flags for the selected language variant. Also it ships with keep system layouts ticked, although it was using US when UK was selected. -- altogether buggy.

---

