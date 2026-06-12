---
title: "Files Manager Missing Window Frame/Global Menu"
date: 2013-10-04
forum: Desktop Environments
---

### Post by mohalim on 2013-10-04
I'm using Ubuntu 13.04. Suddenly Files manager is missing Window  Frame/Global Menu. I have  checked other Application such as Gedit,  Firefox aren't having this  problem. I've tried resetting unity by using  these commands:

dconf reset -f /org/compiz
unity --reset-icons

But the problem still persists.


  Screenshot of the problem:
[IMG]http://i.imgur.com/CvaWyKU.png[/IMG]

Thanks.

---

### Post by Frogs Hair on 2013-10-04
If the file manager or other applications are running  maximized the bar won't be visible and the window buttons appear in the top left corner upon mouse hover. If you are at full screen use F11 or Esc. To restart nautilus use the following command.```
 nautilus -q
```

---

### Post by grahammechanical on 2013-10-04
There are changes to File Manager (Nautilus) in 13.04 that were made by Gnome. I see nothing different in your screenshot as I do when I open and maximise File Manager. There is only one menu in File Manager's global menu and that is File and we see it along with the max, min, close buttons as previously stated by a mouse-over of the top left of the top panel.

To see the other menu options which used to be in a panel at the top of the application window click on the buttons on the top right of the application window.

Regards.

---

