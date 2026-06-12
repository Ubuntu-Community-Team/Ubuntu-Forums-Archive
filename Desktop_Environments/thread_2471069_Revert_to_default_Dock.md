---
title: "Revert to default Dock"
date: 2022-01-20
forum: Desktop Environments
---

### Post by erosman on 2022-01-20
I installed **Dash to Dock** but later decided to remove it. However, there are some changes that has not reverted after removing the extension.

How do I revert to the original Ubuntu Dock?

Also strange thing ....
When **Dash to Dock **is installed but disabled, making changes to its preferences, changes the dock appearance.

PS. The Activities also seems broken now. It used to show multiple desktop with animation now it is blank.

---

### Post by deadflowr on 2022-01-20
Ubuntu Dock *is* dash-to-dock.
To reset run
```
dconf reset -f /org/gnome/shell/extensions/dash-to-dock/
```

---

### Post by erosman on 2022-01-21
Thank you.

The Activities also got sorted after a couple of restarts.

---

