---
title: "Screen resolution"
date: 2006-03-15
forum: Desktop Environments
---

### Post by JW9 on 2006-03-15
My computer updated during the night and now the screen resolution is 640x480, which is way to much for my monitor.  The screen that allows the change will not allow me to change the figures.  Help says to use the dropdown windows to make the change but there are no dropdowns.  Any help will be appreciated.

---

### Post by Ramses de Norre on 2006-03-15
Check your /etc/X11/xorg.conf file, are the right resolutions in it?
You can also try sudo dpkg-reconfigure xserver-xorg

---

### Post by JW9 on 2006-03-15
Neither of these worked.  Does anyone have any other suggestions.  I am completely stumped on this one.  Thanks for trying to help.

---

### Post by frodon on 2006-03-15
Look at your screen specification and get the horizontal and vertical refresh rates parameters of your screen, then add those parameters in your xorg.conf file.
You will details on how to do it here : [http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

EDIT: i forgot to tell you that you will need to restart your xserver to see the changes, you can do with Ctrl+Alt+Backspace

---

