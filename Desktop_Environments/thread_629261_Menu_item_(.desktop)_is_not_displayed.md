---
title: "Menu item (.desktop) is not displayed"
date: 2007-12-02
forum: Desktop Environments
---

### Post by Turin Turambar on 2007-12-02
I mistakenly deleted menu icon of TvTime program. I reinstalled the program, but main menu didn't display it, even though the ".desktop" file was there.

The same happened to Wine. Once I deleted the items with Main menu program and reinstalled Wine, they were not in the panel menu.
Is this a bug?
Is there any program or workaround that can collect .desktop information and bring them back?

---

### Post by Linteg on 2007-12-02
Delete the corresponding files in /home/your_user/.local/share/applications/ and you'll be fine, This is a [reported bug](https://bugs.launchpad.net/ubuntu/+source/alacarte/+bug/118936)

---

### Post by Turin Turambar on 2007-12-02
Thanks! That fixed it. :)

---

