---
title: "Tales of Maj'Eyal Addons"
date: 2019-02-26
forum: Gaming &amp; Leisure
---

### Post by Bike To Australia on 2019-02-26
The game has many, additional,downloadable options that go into 

 /snap/talesofmajeyal/30/game/addons

  
I want to use the GUI to copy and paste what I download into that folder: EASY, CONVENIENT. Using Terminal is not easy or convenient because some addons create conflicts with others or the main game versions I have. BUT, I don't have permission to do anything more than look. How do I "make it so" like Jean-Luc Picard without shaving my head

Ubuntu 18.10, 
I am not using steam to play ToME

---

### Post by oldrocker99 on 2019-02-26
You select the files which you which to copy, and either right-click and select Copy, or hit CTRL-C to copy or CTRL-X to cut, and CTRL-V to paste. The terminal command for moving files as well as renaming them is mv, but it is much easier, as you pointed out, to do it with a file manager,

---

### Post by Bike To Australia on 2019-02-26
I don't have permission, I am not the owner.

---

### Post by Bike To Australia on 2019-02-26
First, I tried this

sudo chown -R bta /snap/talesofmajeyal/30/game/addons
chown: changing ownership of '/snap/talesofmajeyal/30/game/addons/tome-addon-dev.teaa': Read-only file system
chown: changing ownership of '/snap/talesofmajeyal/30/game/addons/tome-items-vault.teaa': Read-only file system
chown: changing ownership of '/snap/talesofmajeyal/30/game/addons/tome-possessors.teaa': Read-only file system
chown: changing ownership of '/snap/talesofmajeyal/30/game/addons': Read-only file system

Then, I tried this

cp -i tome-zomnibus_lite-.teaa /snap/talesofmajeyal/30/game/addons
cp: cannot create regular file '/snap/talesofmajeyal/30/game/addons/tome-zomnibus_lite-.teaa': Read-only file system

---

### Post by deadflowr on 2019-02-26
The /snap directory is a read-only  squashfs loop device mount point.
Even if you could, anything that you would place there would disappear on shutdown.

Usually you could throw related snap configs and what have you into the home snap location.
But I'm not sure how you could do that with what you want to do.

You might need to open an issue over at the github home page for the snap.
[https://github.com/mcphail/talesofmajeyal]("https://github.com/mcphail/talesofmajeyal")
Or open a new discussion at snapcrafters forums.
[https://forum.snapcraft.io/]("https://forum.snapcraft.io/")
Either place would have a far better understanding of how then we would.

Alternatively, you could scour the web for a deb version, which you can then install and through files where you need them without this tye of problem.

---

