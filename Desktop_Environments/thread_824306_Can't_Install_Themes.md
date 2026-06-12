---
title: "Can't Install Themes"
date: 2008-06-10
forum: Desktop Environments
---

### Post by jmhamilt on 2008-06-10
When I try to drag and drop tarballed theme packages onto the Theme Preferences interface, or install/browse/open from inside that interface, I get a "Invalid file type" error and the theme won't install. This has happened with a variety of themes made by different people, all filetype tar.gz. Any suggestions?

---

### Post by acrostic on 2008-06-10
1. Make sure ~/.themes directory is owned by you.

2. Go to [http://gnome-looks.org](http://gnome-looks.org) and download some gtk-2.0 themes

Try the step again as before.

If nothing works extract theme file in /usr/share/themes directly using 

cd /usr/share/themes; sudo tar xvzf path_to_theme_file

Theme should appear when you relaunch apperance settings, possibly under customize option.

---

### Post by jmhamilt on 2008-06-11
Thanks! I'll try that.

---

