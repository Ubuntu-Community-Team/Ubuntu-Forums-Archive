---
title: "Default Unity Icon names/location?"
date: 2013-06-23
forum: Desktop Environments
---

### Post by Jamie_Edwards on 2013-06-23
Hi guys,

I'm trying to make a quick list for Unity to make my launcher look a little less cluttered.

I'd like to know two things if possible,

1 - What are the names of the default icons that Unity uses and if possible, their location? i.e. Games, Adminstration etc.
2 - ( This is more for Steam for Linux ) Where does Steam store the custom launcher .desktop files for installed games?

Thanks

---

### Post by zombifier25 on 2013-06-24
1. Unity uses the icons of the icon theme, in /usr/share/icons. EDIT: For all the categories, look in /usr/share/icons/Humanity/categories/. For your launcher file, you only need the name of the icon for the "Icon" field (for example, applications-games), and the respective icons in your respective icon theme will be used. That's what I managed to find
2. They are in ~/.local/share/applications/. Just about any apps that require user-specific .desktop files store them there.

---

### Post by Jamie_Edwards on 2013-06-24
OK, thanks.

---

