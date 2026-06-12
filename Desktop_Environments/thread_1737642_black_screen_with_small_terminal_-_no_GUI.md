---
title: "black screen with small terminal - no GUI"
date: 2011-04-23
forum: Desktop Environments
---

### Post by cybernetic toaster pastry on 2011-04-23
A friend of mine said he could make my system faster and preceded to kill some processes. I have no idea if that is related but my computer worked fine until I shut it down for a while. When I went back and turned it on it gives me a screen is mostly black with the terminal in the top left corner. If I type "exit" it takes me to the Ubuntu login screen with the colorful background and all. If I sign in it takes me right back to the previous described screen. I dont think it has anything to do with the graphics card or driver because on the login screen and even on the black screen I have a cursor. Plus using nano to view the Xorg log I saw no errors. I have also in desperation removed all Xorg.conf files and remade them and I have tried startx. Please dont tell me I should backup all my files and pop in an image disk and go from scratch

---

### Post by snowpine on 2011-04-23
Try typing:

```
startx
```

Make a note of any error messages and post them back here.

You can also try:

```
sudo apt-get install lubuntu-desktop
```

which will restore any Lubuntu default pacakges that your friend may have deleted.

---

