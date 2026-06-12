---
title: "Set reserved icon for application"
date: 2022-10-21
forum: Desktop Environments
---

### Post by taiwbi on 2022-10-21
Is there anyway to set a reserved icon for .application file? like I have a file with this icon config:
```
Icon=telegram
```
But is there anyway to set a second icon to be shown if the current icon pack doesn't have telegram icon? like this
```
Icon=telegram,/home/user/telegram.png
```
but this doesn't work. 
Is there anyway to do this correctly?

---

### Post by Dennis N on 2022-10-21
You can't have two options on that line. If you have a icon you want to use, you can specify it there by full path and file name. Otherwise, the OS starts looking in your chosen icon theme for a match. Your icon theme can name other themes to check with the **Inherits=** line found in an **index.theme** file located in the theme folder.

---

