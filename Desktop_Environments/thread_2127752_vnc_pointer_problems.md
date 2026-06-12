---
title: "vnc pointer problems"
date: 2013-03-21
forum: Desktop Environments
---

### Post by danielsender on 2013-03-21
I have a Dell Precison M70 on which I updated from 12.04 to 12.10. After that, the unity desktop wouldn't work anymore. I assumed that is was due to the impossibilty of using the proprietary drivers for its old graphic card (NV17GL [Quadro4 500 GoGL]). So I switched to KDE and run it in failsafe mode. That was OK. However I'm having some problems running the vnc servers on it. If I run x11vnc everything is fine. However if I run the regular vncserver, e.g. 'vncserver -geometry 1280x1024 :1', it will work almost everything except when I click on an icon in the panel. For example pressing the left button on the Kickoff Application Launcher will open the menu for just a couple of seconds not giving me time to enter anything. Again, that is not happening with x11vnc.

Any help will be appreciated.

Daniel

---

### Post by danielsender on 2013-03-21
I discover that if I set the panel to "Always visible" then the problem does not occur, but if I set it to "Autohide" then it disappears after a couple of seconds. As I said in my initial posting, If I use x11vnc then the problem does not occur, I can have "Autohide" and when I click on the "Kickoff Application Launcher" it will stay on.

---

