---
title: "Unity Breakdown"
date: 2011-11-28
forum: Desktop Environments
---

### Post by popejeremy on 2011-11-28
I logon to the default Unity in Oneric and I get this:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=208183&stc=1&d=1322537177[/IMG]

The left-hand menu is completely gone and none of the icons on the top menu are there either. It's basically just an empty screen with a desktop background.

If I login to Ubuntu 2D everything is fine, but the default GUI is borked. What can I do to fix it?

---

### Post by typhoon_tip on 2011-11-28
Open the terminal (in these conditions, you can do it with the above menu), and do:

```
ccsm
```

If is not installed:

```
sudo apt-get install compizconfig-settings-manager
```

Find the Unity Plugin, and tick it again, everything should re-appear. If it doesn't appear, try this:

```
unity --reset
```

---

