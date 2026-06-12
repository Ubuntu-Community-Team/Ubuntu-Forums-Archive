---
title: "Where are things downloaded through the package manager located?"
date: 2009-02-21
forum: General Help
---

### Post by skunkONE on 2009-02-21
So I downloaded this game called Flightgear through the package manager. I downloaded more planes for the game but I cant find where the game is installed so I cant put the new planes in the game..

So my question is where are items downloaded through the package manager located when they are downloaded?

---

### Post by lykwydchykyn on 2009-02-21
> **skunkONE said:**
> So I downloaded this game called Flightgear through the package manager. I downloaded more planes for the game but I cant find where the game is installed so I cant put the new planes in the game..

So my question is where are items downloaded through the package manager located when they are downloaded?

If you open synaptic and locate the package you installed, you can right-click on it and select "properties".  There's a tab in the properties dialog that will list installed files.

If you want a quicker method, you can install the command line tool "apt-file".

---

### Post by skunkONE on 2009-02-21
Ah...Found it.

Thank you friend :)

---

### Post by mcduck on 2009-02-22
Everything gets installed not based on what program it belongs to but what's the purpose of the file.

Most of the time you'll find the program's executable file in /usr/bin, launcher icon in /usr/share/pixmaps, documentation in /usr/share/doc, and so on. All the files that have no beter place in the file system goe to /usr/share/*nameoftheprogram*.

Since each user can usually configure program settings independently from other users, programs often create their own configuration files in every user's home directory (as hidden files or directories). Quite often programs that use plugins or allow adding extra features also support adding them at user level, in which case they are also installed into these hidden directories inside your home dir.

---

