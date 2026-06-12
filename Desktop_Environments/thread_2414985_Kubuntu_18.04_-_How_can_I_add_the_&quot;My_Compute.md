---
title: "Kubuntu 18.04 - How can I add the &quot;My Computer&quot; icon on the Desktop?"
date: 2019-03-18
forum: Desktop Environments
---

### Post by aquerci on 2019-03-18
is there a way to add the "My Computer" icon on the Kubuntu's Desktop like happen in Windows? most linux distributions can reach the "My Computer" folder using the path "computer:///" but when I try to open that folder via Dolphin, it seems that it can't find it. how can I reach that folder? where is the issue and how can I pin it on my Desktop?

---

### Post by SeijiSensei on 2019-03-18
I don't know about other distributions, but there is no fundamental difference between "My Computer" and the directory tree that appears when you click the "root" option in the left-hand pane in Dolphin.  Unlike Windows with its drive letters, all resources in Linux are mounted into the directory tree.

Also as an ordinary, non-root user, you can't alter anything outside of $HOME, /tmp, and mounted devices to which you have permissions.

---

### Post by aquerci on 2019-03-21
yeah, but I prefer to have all mounted devices in a single folder like happen in Windows, in Linux Mint Cinnamon, Ubuntu MATE, and in most others important Linux distributions. for example, in this screenshot you can see the "My Computer" icon pinned on the desktop and his content in Ubuntu MATE 18.04:

[[IMG]http://thumbs2.imagebam.com/ba/5f/06/9dca521170307894.jpg[/IMG]]("http://www.imagebam.com/image/9dca521170307894") 


I would very like have the same thing in Kubuntu. is it possibible?

---

### Post by SeijiSensei on 2019-03-21
I think you can create a folder in the left-hand pane of Dolphin. Then you can drag-and-drop whatever objects you want into that folder.

---

### Post by aquerci on 2019-03-21
> **SeijiSensei said:**
> I think you can create a folder in the left-hand pane of Dolphin. Then you can drag-and-drop whatever objects you want into that folder.
sorry but I don't understand your reply. I don't want to add a new folder in the Dolphin side panel and then put others objects inside it. my goal is completely different. I want to have a "My computer" icon in my desktop. what does it mean? It means a folder on my desktop, with a computer icon, where you can find all mounted drivers. To be clear, I want to reach the same situation that you saw in my screenshot with Ubuntu MATE. Kubuntu (Ubuntu with KDE) and Ubuntu MATE works with the same source code, so I think if the first can do it, probably also the second can do the same thing, or not?

---

### Post by CatKiller on 2019-03-21
> **aquerci said:**
> To be clear, I want to reach the same situation that you saw in my screenshot with Ubuntu MATE. Kubuntu (Ubuntu with KDE) and Ubuntu MATE works with the same source code, so I think if the first can do it, probably also the second can do the same thing, or not?

That function is provided by Gnome's file manager, Nautilus, which handles the desktop. Mate was based on Gnome 2, so its file manager behaves similarly.

KDE is an entirely different project, from entirely different people, with entirely different goals and priorities. KDE's file manager doesn't even handle the desktop.

There is absolutely no reason to expect that features from one desktop environment would necessarily be included in the other. Approaching things differently is the point of having different desktop environments in the first place.

There are probably several removable drive plasmoids to choose from for display on your KDE desktop.

---

