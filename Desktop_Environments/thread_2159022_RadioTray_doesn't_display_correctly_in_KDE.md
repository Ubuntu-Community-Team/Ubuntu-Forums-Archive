---
title: "RadioTray doesn't display correctly in KDE"
date: 2013-07-01
forum: Desktop Environments
---

### Post by Erik1984 on 2013-07-01
I've used RadioTray before in Kubuntu and back then it worked. Now when I launch radiotray with 13.04 I get a missing 'app indicator' and the menu is not displayed as it should

[[IMG]http://i.imgur.com/hBAsQ2Z.png[/IMG]](http://imgur.com/hBAsQ2Z)

Kubuntu version 13.04
KDE 4.10.4
GTK2 and 3 theme: oxygen-gtk

---

### Post by dino99 on 2013-07-02
sudo apt-get install python-appindicator

---

### Post by Erik1984 on 2013-07-02
Thanks, but that package is already installed:
```

python-appindicator:
  Installed: 12.10.1daily13.04.15-0ubuntu1
  Candidate: 12.10.1daily13.04.15-0ubuntu1
  Version table:
 *** 12.10.1daily13.04.15-0ubuntu1 0
        500 http://nl.archive.ubuntu.com/ubuntu/ raring/main amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by buzzingrobot on 2013-07-02
This is from memory, but....

RadioTray's config file is in your home directory:  ~/.local/share/radiotray/config.xml.

If you open it in an editor, you'll see this line:```
  <!-- valid options are 'appindicator', 'systray' and 'chooser' -->

```

If the line immediately below shows
 ```
value=appindicator
``` change "appindicator" to "systray".  Save the file and restart RadioTray and see if the usual icon appears in the panel.

---

### Post by Erik1984 on 2013-07-02
Thanks buzzingrobot! That fixed it. The indicator and the menu now display as they should :)

---

