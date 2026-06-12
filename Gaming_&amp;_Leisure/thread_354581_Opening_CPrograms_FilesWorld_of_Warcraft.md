---
title: "Opening C:/Programs Files/World of Warcraft"
date: 2007-02-06
forum: Gaming &amp; Leisure
---

### Post by DaveyV on 2007-02-06
Well i got World of Warcraft installed using Wine 0.9.30. Im trying to opend the realmlist.wtf  but im now sure how to and search within Wine directories?

---

### Post by Sammi on 2007-02-06
Wine's fake c: drive is found at /home/*<username>*/.wine/drive_c/

You should be able to edit config.wtf by running this command in a terminal:
```
gedit ~/.wine/drive_c/Program\ Files/World\ of\ Warcraft/WTF/config.wtf
```Where ~ is short  for /home/*<username>*/ and *<username>* is your computer login user name of course.

---

### Post by DaveyV on 2007-02-06
Thx for the reply. I tried the command to configure  the config.wtf but i can't save. I want to change the realmlist too.

---

### Post by Sammi on 2007-02-06
Sounds like you aren't the owner of the file. Did you run the installation with the sudo command in front?

Sudo means that that command is run with administrator rights, and if you did this then the administrator now incorrectly stands as the owner.

You can give youself read/write rights to your WoW directory by doing the following commands in a terminal:
```
sudo chown -R mike:mike /home/mike./wine/drive_c/Program\ Files/World\ of\ Warcraft/
cd ~/.wine/drive_c/Program\ Files/World\ of\ Warcraft/
sudo chmod 644 *
```Remember to change **mike** to your own computer login name.

---

### Post by DaveyV on 2007-02-06
Thx mate! ima try that wen i go home.

---

### Post by Jengu on 2007-02-06
Did you copy WoW from your windows NTFS partition? The files might be all marked read only. If you're trying to _play_ WoW directly off your windows partition, that for sure won't work, at least not without NTFS write support (you can find howto's for that by searching the forums, but it'd probably just be best to copy WoW to your linux partition instead).

---

### Post by DaveyV on 2007-02-06
Sorry i was at school. No i directly transfer the data from a cd onto a WoW file in my home.

#I got it fixed, but now i have now image wen in the server the game is black except for the action bar below and the map top right corner They seem distorted or brightly lit. I'm going to see if i can find an answer.

---

### Post by Sammi on 2007-02-06
Are you running in d3d or opengl mode?

Have you seen the [Ubuntu community WoW/Wine wiki]("https://help.ubuntu.com/community/WorldofWarcraft")?

---

### Post by DaveyV on 2007-02-06
Yea i  looked inside that website. I am not sure if im running under D3D or openGL. Maybe D3d. How can i check?

---

### Post by Sammi on 2007-02-06
It depends on which one of these two lines you have in your config.wtf:

SET gxApi "OpenGL"
SET gxApi "d3d"

---

### Post by DaveyV on 2007-02-06
Its set to openGL. Should i instead use D3D? And if so i just replace the openGL to D3D and wat do i have to reconfigure?

---

### Post by DaveyV on 2007-02-06
Ok i tried setting to D3D and back to OpenGL and i still do not get anything, I'm going to try to reinstall WoW again hopefully things work.

---

