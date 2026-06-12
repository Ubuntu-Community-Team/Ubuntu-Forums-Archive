---
title: "Install help"
date: 2006-11-26
forum: Gaming &amp; Leisure
---

### Post by dmb83fan41 on 2006-11-26
I am new to ubuntu and would like to learn how to install games from a zip version.  I have no idea what to type in the terminal to install and open the games.  For example I would like to install this "legacy_142_linux.tar.gz" which is a legacy version of Doom.  I really want to get Doom up and running.  Any help would be greatly appreciated! Thanks!!

---

### Post by finferflu on 2006-11-26
To untar the archive, first make sure you are in the directory where the archive is, let's say it's in your Desktop, you should do:

```
cd /home/<your username>/Desktop
```

then extract the files with this command:

```
tar -zxvf legacy_142_linux.tar.gz
```

This will create the folder legacy_142_linux/ in your currend working directory (in this case /home/<your username/Desktop).

Usually installation instructions are in a README or INSTALL file in the archive. You should always check whether there is an Ubuntu package available, which makes things a lot easier.

By the way, an easy way to untar an archive is double clicking on it ;)

---

