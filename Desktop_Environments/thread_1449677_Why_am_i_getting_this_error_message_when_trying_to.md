---
title: "Why am i getting this error message when trying to install new themes?"
date: 2010-04-08
forum: Desktop Environments
---

### Post by Macfunky on 2010-04-08
I customised a theme and made it into a .tar.gz file. When i try to install it i get the following error message. 


Installation for theme "Theme" failed.

Can't move directory over directory


At first i thought, seeing as i tweaked a current theme from gnome-look, that i may have done something wrong that will not allow it to install so i tried it with other themes i downloaded and i get the same message with everyone it seems. Anyone know what could be wrong and what i can do about it? Thanks

---

### Post by mcduck on 2010-04-08
Either you already have a theme with the exact same name installed, or the contents (and especially the *directories*) of the .tar.gz package you made aren't arranged in correct way.

---

### Post by micio on 2010-04-08
this error can occour where you are upgrading a theme... many times they use the same folder name

IE. you are using mytheme v1.0 and want install the mytheme v 2.0

both are using a simple folder called mytheme

so try to rename the folder /home/user/.themes/mytheme in /home/user/.themes/mythemeOLD and then install the new theme.

bye

Micio

---

### Post by shaka_zulu on 2010-04-08
I agree with it. But give man a solution for this problem :)

---

