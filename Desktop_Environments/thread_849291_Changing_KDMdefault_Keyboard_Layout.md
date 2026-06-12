---
title: "Changing KDM/default Keyboard Layout"
date: 2008-07-04
forum: Desktop Environments
---

### Post by DWRZ on 2008-07-04
during my fresh reinstall of 8.04, i accidentally selected dvorak classic instead of dvorak international.

i've been able to switch the layout to dvorak international via the kde system settings. it works-- except for kdm. for some reason there the dvorak classic layout stays.

how can i change the layout to dvorak classic? i have a lot of symbols and numbers in my password and it's a bit of a pain.

---

### Post by pluviosity on 2008-07-17
You are going to need to change the layout in your xorg.conf file, under the Input Device section for the keyboard.  I do not know what the option is for international Dvorak...anyone else have any ideas?

---

### Post by DWRZ on 2008-07-17
Yeah. That should do it, as it is set in dvorak-classic right now.

I'm thinking it should be either: dvorak, dvorak us, or dvorak-intl us. But not sure. :\

---

