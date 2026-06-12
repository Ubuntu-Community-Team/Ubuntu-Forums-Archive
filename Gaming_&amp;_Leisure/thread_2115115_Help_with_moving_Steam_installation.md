---
title: "Help with moving Steam installation"
date: 2013-02-11
forum: Gaming &amp; Leisure
---

### Post by ALEXALEX1432 on 2013-02-11
Hi everyone,

I have my /home directory on an SSD and I have an 2tb HDD I would want my steam install to be on.  I've googled around to do this and people were saying "just move the 'Steam' folder in your home directory and start steam and it'll ask you to find it"

Well I never got that prompt and I don't have a Steam folder in my home directory. The only one I did have was a ./steam folder (a hidden one) and every time I moved it and started steam, it was re-created.

Any and all help is appreciated

---

### Post by holastickboy on 2013-02-12
The folder you referring to isn't actually where steam keeps its appfiles.  The actual folder is in your home folder, and is located at /home/YOURUSERNAME/.local/share/Steam

From there, the SteamApps folder is the folder with the applications. I have recently reinstalled my Ubuntu, and backed up this file. When I reinstalled Steam, it recreated its files again, but I put my backup in the new location.  When you install a game that you know you have a cache of, you will still have to double click to install it.  That being said, however, Steam will do a "Discovering existing files" and the installation will not download any files.

The other method when installing the game is that it gives you the option to install it to any location you like (for future installs).

---

