---
title: "Problem With The Workspace Switcher on Ubuntu 11.10"
date: 2012-01-03
forum: Desktop Environments
---

### Post by tkabir11 on 2012-01-03
I recently installed Ubuntu 11.10 on my machine- all is well except for a little problem with the workspace switcher. When I have two windows open side-by-side (you know when you *drag* each window to the edge of your screen and make it fit in half of your screen), then if I try to switch to a new desktop using the workspace switcher- those two windows move to that new desktop....if you know what I mean :| Is there a way to fix this? Or is it a glitch in ubuntu 11.10- or is it just meant to be like that? :confused:

Btw- this doesnt happen when I have those two windows running without doing the drag-and-fit thingy...ie- they stay in the desktop they were opened in.

---

### Post by innabawks on 2012-01-05
Ever since I let the update manager install a bunch of updates, the Workspace switcher doesn't work anymore. I tried resetting the unity desktop, and noticed a couple of BUGGY CLIENT messages in the logs. I'm thinking that either some updates didn't install properly, or some updates just need to be removed.

---

### Post by innabawks on 2012-01-05
Actually, I ran the synaptic update manager and selected all the Unity updates and told it to reinstall them. Rebooted the computer, and my workspace switcher is working again.

---

### Post by tkabir11 on 2012-01-06
Well I was actually using the ''seamless mode'' in Virtualbox- and looks like that was the culprit. Since I was only trying out the seamless mode- I won't be using it anymore since I prefer using vb standalone. Didn't have the problem anymore after reboot.

---

