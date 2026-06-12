---
title: "html desktop shortcut opens in gedit"
date: 2009-05-11
forum: General Help
---

### Post by planecharlie on 2009-05-11
Hi,

I don't know how I messed this up. This just started today, and I don't know how to change it. I have a number of shortcuts on my desktop to specific websites (looking for a job). I check these websites daily for updates. This morning each link I click opens in gedit. Right click doesn't give me an open with option. If I log into another user account, desktop html shrortcut links work properly. I cant find anywhere in preferences a way to change this behavior. Any ideas?

Thank You,
Charlie

---

### Post by VCoolio on 2009-05-11
Don't know the problem but as a workaround you can paste following in gedit and save as openwithfirefox.sh in ~/.gnome2/nautilus-scripts

```
#!/bin/sh
firefox $NAUTILUS_SCRIPT_SELECTED_URIS
```

Now rightclick on the file, and in scripts you find openwithfirefox, which, when clicked, will open your file in firefox. 
When it doesn't work you need to give the file permissions with

```
sudo chmod u+x ~/.gnome2/nautilus-scripts/openwithfirefox.sh
```

Good luck with the real problem.

---

