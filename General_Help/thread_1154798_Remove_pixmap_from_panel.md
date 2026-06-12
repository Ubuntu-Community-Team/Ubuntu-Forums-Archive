---
title: "Remove pixmap from panel"
date: 2009-05-10
forum: General Help
---

### Post by MysticalRiotCandy on 2009-05-10
I have my Gnome-panel set up vertically, and I have User Switcher as an Applet on.  But, it wants to keep displaying this image.  
[IMG]http://img21.imageshack.us/img21/769/usersocj.png[/IMG]

I want to find the pixmap for it and keep it from loading.  Either by modifying the applet to not show an image, or by deleting the image.  I don't know which, and I don't know where either are located.

---

### Post by Legace on 2009-05-10
Don't know if this works for the fast user switcher applet, but you can try :)
You can set custom icon for that applet via gconf-editor.

Enter in Terminal:
```
gconf-editor
```

Browse to **/apps/panel/applets/fast_user_switch_screen0** and there will be a value for **custom_icon**.
Make sure to check use_custom_icon.

---

### Post by CatKiller on 2009-05-10
Icons (desktop, menu and panel) are determined by the icon theme that you're using. The icon images are kept in /usr/share/icons/<ThemeName> (if you're using one of the packaged ones) or ~/.icons/<ThemeName> (if you're using a theme you've installed yourself).

Each theme doesn't necessarily have icons for every possible use included, so they "inherit" the icons from other themes to fill in the gaps. For example, the Human theme inherits the icons from Tangerine and gnome. You could provide an icon that you prefer for the theme that you're using; that should then be used rather than the generic gnome one. I believe it's the /stock/generic/stock_people icon that gets used. In principle, you should be able to provide a transparent image of the appropriate size to have no icon displayed at all if you'd prefer that to just having a nicer icon.

---

