---
title: "Unity 2d 10.10 - How does one move the launcher icons?"
date: 2011-03-17
forum: Desktop Environments
---

### Post by incogweedo on 2011-03-17
Hey guys, long time lurker here.  I was just wondering how I could reorder/drag n drop/move the unity-2d (qt version) icons in ubuntu 10.10, like you would in the mutter version unity.  I can move the launcher up and down, I just can't pull them off the launcher and drag them around.  Is this a bug or has it just not been implemented yet?  Other than this, I love unity 2d and can't wait for the compiz-based unity 3D to use in 11.04

Thanks in advance :)

---

### Post by incogweedo on 2011-03-17
Is there seriously no one out there with an answer?

---

### Post by ranger12 on 2011-03-20
I was wondering about that myself. It looks like according to the launchpad site - it was added only to the Unity-2d 3.6 branch which I think is for Natty. I did update unity-2d via the update-manager yesterday and noticed that the autohide/intellihide featrue and the nice glowing effect has been added. They also changed the background to the launcher. It matches the one in Natty so I do not know if it is supposed to be transparent or not but if it is, it is not working on my system unless there is a setting in the qml file for it.

---

### Post by ranger12 on 2011-03-22
Ok I just got an answer on this from Oliver over at the unity-2d launchpad site. He states that dropping desktop files on the launcher to add to favorites works on both Macerick and Natty but dragging tiles to reorder them on the launcher only works in Natty.

---

### Post by ankspo71 on 2011-03-23
Hi,
I just figured this out on accident...
In Natty with Unity 2D, we can hold down the left mouse button on the icon we want to move for about 2 seconds, then the icon will detach from the dock, then we can freely move it. I haven't tried this in Unity 3D yet.

---

### Post by n.williams0440 on 2011-03-23
Ok I just got an answer on this from Oliver over at the unity-2d  launchpad site. He states that dropping desktop files on the launcher to  add to favorites works on both Macerick and Natty but dragging tiles to  reorder them on the launcher only works in Natty, Thanks......

---

### Post by L'ami Francais on 2011-03-24
to reorder the icon in Unity-2D in Maverick, use the gconf-editor.
- open a terminal.
- type in: gconf-editor
- in the editor go to: desktop/Unity-2D/Launcher
- right click on the key called "Favorite" and select "edit key".
- you get a new dialog with a list. select the item you want to move then up or down.
- select "ok"
- close the editor
- back in the terminal window type: killall unity-2d-launcher
that will restart unity and you will have the icon in the new order.
hope that helps.
Nicolas

---

### Post by GECKYL on 2011-10-05
> **ankspo71 said:**
> Hi,
I just figured this out on accident...
In Natty with Unity 2D, we can hold down the left mouse button on the  icon we want to move for about 2 seconds, then the icon will detach from  the dock, then we can freely move it. I haven't tried this in Unity 3D  yet.

BINGO!  Thanks...:guitar:

---

### Post by popeye on 2011-11-03
Thanks as well, was searching for ages how to fix this.  :P

---

