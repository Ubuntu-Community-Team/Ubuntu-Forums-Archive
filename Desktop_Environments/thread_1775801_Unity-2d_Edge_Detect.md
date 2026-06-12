---
title: "Unity-2d Edge Detect"
date: 2011-06-05
forum: Desktop Environments
---

### Post by pauljwells on 2011-06-05
On my HP Netbook, Unity will run, but uses too much cpu, slows down the system and makes it run too hot.

I installed Unity-2d, which is a better compromise for this machine but unlike Unity-3d the launcher only shows when you mouse over the top-left corner rather than at the left edge of the screen.

This is a bug and the devs have written a fix that will be included in 11.10 but I went ahead and compiled a set of debs to add this feature to the current code.

They are here: [http://dl.dropbox.com/u/18375146/unity-2d-edge-detect.tar.gz]("http://dl.dropbox.com/u/18375146/unity-2d-edge-detect.tar.gz")

Best to install via terminal:

```
sudo dpkg -i ./*.deb
```

If you want to go back to the defaults all you have to do is 'mark all upgrades' in synaptic.

If you run unity-2d and you find that the first item on the launcher keeps losing its tooltip please add yourself to this bug report.

[https://bugs.launchpad.net/ubuntu/+source/unity-2d/+bug/758787]("https://bugs.launchpad.net/ubuntu/+source/unity-2d/+bug/758787")

---

