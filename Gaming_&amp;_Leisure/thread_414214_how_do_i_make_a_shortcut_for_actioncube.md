---
title: "how do i make a shortcut for actioncube?"
date: 2007-04-19
forum: Gaming &amp; Leisure
---

### Post by super.rad on 2007-04-19
i installed actioncube from this guide

sudo apt-get install build-essential libsdl1.2-dev libsdl-image1.2-dev libsdl-mixer1.2-dev

Note: Please check the ActionCube website for updates: [http://action.cubers.net/download.html](http://action.cubers.net/download.html) Download the game here by clicking on ActionCube v0.92 for Linux/Unix. Change to the directory where you downloaded the game.

tar xvf ActionCube_*.tar.bz2
cd ActionCube/source/src/
make install
cd ../../
./actioncube.sh


but i dont have an icon for it and its not on any of the menus, how do i add it to the game menu or make a shortcut on the desktop for it?

---

### Post by askreet on 2007-04-19
I dont know much about this, but it appears that a script to launch the game called actioncube.sh resides in your home folder, is that correct?

In any event, right click on your desktop and select Create Launcher.  In the command box enter ~/actioncube.sh

You can enter anything you like for the Name and Description fields.  Try that and let me know how it works for you.

---

### Post by super.rad on 2007-04-19
im getting an error that says:

Details: Failed to execute child process "~/actioncube.sh" (No such file or directory)

found out that "actioncube.sh" isnt in the home directory its in /home/mole/Desktop/ActionCube
tried changing the command to /home/mole/Desktop/ActionCube/actioncube.sh but just did nothing

---

### Post by askreet on 2007-04-19
Then it appears I was mistaken, you need to locate the executable for the game/program.

Let me see if I can find out where it defaults to.. unless it asked you.

EDIT:

I wasn't able to find out where the executable goes.  You can try this:

-  Open a terminal
- Change directory to /  (type: cd /)
- Type: find |grep actioncube

This will show you all the files and directories with 'actioncube' in it.  If you paste the results here, I can take a stab at which one is the executable.

- Kyle

---

### Post by RomeReactor on 2007-04-19
Hi. Try entering this in the command field of the launcher:

```
sh -c "cd /home/mole/Desktop/ActionCube && ./actioncube.sh"
```

---

### Post by super.rad on 2007-04-19
./home/mole/Desktop/ActionCube/actioncube.sh
./home/mole/Desktop/ActionCube/source/xcode/actioncube-Info.plist
./home/mole/Desktop/ActionCube/source/xcode/actioncube.icns
./home/mole/Desktop/ActionCube/source/xcode/actioncube.xcodeproj
./home/mole/Desktop/ActionCube/source/xcode/actioncube.xcodeproj/project.pbxproj
./home/mole/Desktop/ActionCube/source/xcode/actioncube.xcodeproj/julianmayer.pbxuser
./home/mole/Desktop/ActionCube/source/xcode/actioncube.xcodeproj/julian.pbxuser
./home/mole/Desktop/ActionCube/source/xcode/actioncube.xcodeproj/julian.perspective
./home/mole/Desktop/ActionCube/source/xcode/actioncube.xcodeproj/julianmayer.perspective
./home/mole/Desktop/ActionCube/actioncube_server.sh

---

### Post by super.rad on 2007-04-19
Thanks RomeReactor worked perfectly

---

### Post by fakie_flip on 2007-04-20
That worked good. Thanks.

---

