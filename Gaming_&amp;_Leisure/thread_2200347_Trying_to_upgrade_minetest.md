---
title: "Trying to upgrade minetest"
date: 2014-01-18
forum: Gaming &amp; Leisure
---

### Post by grier-devon on 2014-01-18
I am currently running a build of 0.4.7 of minetest and I am trying to upgrade to version 0.4.9, I have been...
```
sudo apt-get purge minetest*
sudo add-apt-repository ppa:minetestdevs/stable
sudo apt-get update
sudo apt-get install minetest
```

When I turn the game on it says I am still using 0.4.7 when according to launchpad minetest show they have 0.4.9 available. Any ideas on how to get this upgrade to 0.4.9 other then waiting on Ubuntu 14.04?

---

### Post by spencer the great on 2014-01-19
Are you willing to download minetest from their website and manually install it?

Download:
```
$ curl -L -o minetest.zip https://github.com/minetest/minetest/releases/download/0.4.9/minetest-0.4.9.zip
```


Extract (minetest.zip should include its own subdirectory, just tested, won't clutter up your active directory):
```
$ unzip minetest.zip
```

Enter the newly created folder:
```
$ cd minetest-0.4.9
```

Compile:
```
$ cmake .
$ make
```

And there you go! To run:
```
$ cd minetest-0.4.9
$ bin/minetest
```

You can always create a shortcut/launcher to the minetest binary in /home/USERNAME/minetest-0.4.9/bin/minetest. So you don't have to open a terminal every time you want to play mt.  I know I do... I'm addicted to terminals :P

---

### Post by grier-devon on 2014-01-19
Thank you so much, I have ran into a small snag, when I get to the part of
```
cmake .
```
I am getting 
> CMake Error: The source directory "/home/devon/minetest-0.4.9" does not appear to contain CMakeLists.txt.
Specify --help for usage, or press the help button on the CMake GUI.

---

### Post by LillyDragon on 2014-01-19
You can always uninstall the game, and reinstall it with packages manually downloaded from the official PPAs too. That's what I do for each new version of the game. Since it doesn't delete my personal .minetest folder, upgrading is as simple as clicking on the new package and upgrading.

---

### Post by grier-devon on 2014-01-19
Is that not what I did in the first post?

---

### Post by grier-devon on 2014-01-19
Got it, I was suppose to after the purge and adding the ppa I should have...
```
sudo apt-get install minetestc55
```

---

