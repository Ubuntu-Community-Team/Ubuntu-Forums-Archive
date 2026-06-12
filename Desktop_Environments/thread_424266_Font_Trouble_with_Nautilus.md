---
title: "Font Trouble with Nautilus"
date: 2007-04-26
forum: Desktop Environments
---

### Post by illuminati11_13 on 2007-04-26
How does one change the font settings in Nautilus for a certain user? Nautilus only prints boxes when I run it as my main user. Root doesn't have this problem so I know it's a user setting issue, but i don't know where the break is.

This is also an issue with the desktop menu's I've just discovered. It seems to be a problem with my gnome user settings?

---

### Post by packjamNL on 2007-05-07
in your terminal type gconf-editor, scroll till nautilus, there are your font settings, wich are the same you set with your font settings in the menu.

---

### Post by metalheart on 2007-05-07
To Restore Default Preference Values

> To restore the default preference values for a user, run the following command:

# gconftool-2 --direct --config-source user-configuration-source --recursive-unset

Replace user-configuration-source with the configuration source in the .gconf directory in the home directory of the user.

This command resets the values of all preference keys, in all subdirectories, from the user setting to the setting in the default configuration source. 

---

