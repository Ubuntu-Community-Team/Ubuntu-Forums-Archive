---
title: "Xubuntu: How to backup Panel custom configuration"
date: 2013-04-10
forum: Desktop Environments
---

### Post by UranUtan on 2013-04-10
Hi,

I spent quite sometimes to configure my two panels. Especially the launchers that I created one by one. I would like to save all these settings for backup purposes. Can you please show me the location where I can save these XFCE Panel Custom settings?

Thanks in advance for any help.

---

### Post by brainwash on 2013-04-11
The user-specific Xfce Panel configuration file is located here:
```
/home/<user>/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-panel.xml
```
This folder contains the item-specific configurations (e.g., launchers, mailwatch settings):
```
/home/<user>/.config/xfce4/panel
```

---

