---
title: "Disable Global App Menu in Unity"
date: 2011-05-25
forum: Desktop Environments
---

### Post by Mushaf on 2011-05-25
Unity comes with a feature that all the applications show their menus in the panel and not in the application window, similar to mac. This is quite irritating to me. I want to see the menus in the application window. Those who feel the same like me here's an easy way to disable the global appmenu in unity. Open terminal and run the following command -

```
sudo mv /usr/lib/indicators/5/libappmenu.so /usr/lib/indicators/5/libappmenu.so.old
```Then restart panel
```
killall unity-panel-service
```In case you want to get the global appmenu back run this command -
```
sudo mv /usr/lib/indicators/5/libappmenu.so.old /usr/lib/indicators/5/libappmenu.so
```And restart panel
```
 killall unity-panel-service 
```

If panel restarting doesn't work logout session and login again.

---

