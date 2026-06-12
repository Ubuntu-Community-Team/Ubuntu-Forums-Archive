---
title: "mouse themes"
date: 2010-05-07
forum: Desktop Environments
---

### Post by Joe Awsome on 2010-05-07
How do I install X11 mouse themes in Lubuntu 10.04 beta 3? I would really apreciate it of someone could help.

---

### Post by llelectronics on 2010-05-09
1. Download Theme
2. Extract to ~/.icons
  2.1 Create the folder .icons if it does not exist in your home folder. 
  2.2 It is a hidden folder so hit CTRL+H to view hidden folders.
3. Open up a Terminal
4. Type in 
```
sudo update-alternatives --config x-cursor-theme
```
5. Choose the newly installed theme by entering the right number representing the new theme. 
6. Restart Xorg by loggin out and back in again or restart

---

