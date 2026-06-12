---
title: "crossover office  install"
date: 2005-04-27
forum: Desktop Environments
---

### Post by kisain on 2005-04-27
i went to the codeweavers website and downloaded crossover office but when i try to install it it says: gedit was not able to automaticly detect the charicter coding. please, check that you are not trying to open a binary file and try selecting a charicter icodeing in the 'opent file....' (or open location) dialog, 
ok so what am i doin wrong here? and anyone know if crossover isen't possible how to install a .exe in wine?

---

### Post by bored2k on 2005-04-27
I don't know howd you install it, but this is it :

- If you downloaded the .sh, do [in a terminal window] chmod 755 filename.sh, then ./filename.sh.
- If you downloaded a .deb file, sudo dpkg -i filename.deb
- If you downloaded a .rpm file, try to get the .deb, if not, sudo alien -d filename.rpm, then sudo dpkg -i newfilename.deb

After it is installed, a menu will appear on your panel. I have winrar , winmx and MS Office so yes it opens .exe files.

You can also download wine and simply do wine filename.exe to run the desired application.

---

### Post by Anonymo on 2005-06-18
Thank you so much

this worked perfectly

---

