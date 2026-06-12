---
title: "how to install themes?"
date: 2009-04-17
forum: Desktop Environments
---

### Post by JakeHinojosa on 2009-04-17
i downloaded some themes and i tried to install them, but it always says its an invalid theme. im downloading them from gnome-look.org , so why is it not working?

it only works on some themes.

---

### Post by Daisuke_Aramaki on 2009-04-17
Its likely that the archive has subfolders, with different flavors of the themes, so you cannot drag and drop just like that. Best way to do that is to extract the archive. and check the contents of the folder. If you see multiple subfolders inside the extracted folder, have a look in them and check for the folders that have a subfolder called gtk-2.0 or metacity for example. these are the theme folders. The local theme folder will be at /home/yourusername/.themes Just move the folders containing the gtk-2.0 subfolders to your .themes folder, and then when you look into to your appearances dialog, the theme will be there.

---

### Post by JakeHinojosa on 2009-04-17
> **Daisuke_Aramaki said:**
> Its likely that the archive has subfolders, with different flavors of the themes, so you cannot drag and drop just like that. Best way to do that is to extract the archive. and check the contents of the folder. If you see multiple subfolders inside the extracted folder, have a look in them and check for the folders that have a subfolder called gtk-2.0 or metacity for example. these are the theme folders. The local theme folder will be at /home/yourusername/.themes Just move the folders containing the gtk-2.0 subfolders to your .themes folder, and then when you look into to your appearances dialog, the theme will be there.

ok, i did what you said and it worked, thanks for your help!

---

