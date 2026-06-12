---
title: "Put icon on side bar"
date: 2013-08-24
forum: Desktop Environments
---

### Post by Ronaldo_Lanhellas on 2013-08-24
Well, I installed Eclipse on my ubuntu 13.04, in the folder: /usr/local/eclipse. If i type the command: "./ecplise" i launch the eclipse normally, but i wanna put this application in side bar of ubuntu. how can i do it ?

---

### Post by stinkeye on 2013-08-24
Install the old main menu (alacarte).
You also need to install gnome-panel for the create a launcher dialogue.(installs gnome-desktop-item-edit)

Install via terminal...
```
sudo apt-get install --no-install-recommends gnome-panel alacarte
```

Search for alacarte in the dash and open.
Choose a section in the left column and then select **New Item** to open the create launcher dialogue.
Be aware that the create launcher dialogue opens up behind the main menu window for me.

Create your launcher. Choose an icon by clicking the icon to the left in the create launcher dialogue.
Then search in the dash for your launcher name or comments.
Drag your launcher from the dash to the launcher panel.

---

