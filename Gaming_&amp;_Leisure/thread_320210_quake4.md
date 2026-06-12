---
title: "quake4"
date: 2006-12-16
forum: Gaming &amp; Leisure
---

### Post by eisle89 on 2006-12-16
I'm duel booting Win x64 and Edgy. From Windows I copied the pk4 files from my Q4 CD's to a 32fat partition. I'm trying to copy these files to my existing /usr/local/games/quake4/qbase folder. I've already run the quake4-linux-1.3-2.run file where the rest of the install correctly sits. I can't seem to become allowed to copy these files with " sudo cp /sda3/q4base/pak001.pk4 /usr/local/games/quake4/q4base" Any help is greatly needed TIA

---

### Post by pay on 2006-12-16
Try ```
sudo ln -s /sda3/q4base/* /usr/local/games/quake4/q4base
```That makes a symbolic link without copying the files.

---

### Post by eisle89 on 2006-12-16
That knocked me to 640x480 fromm 1600x1200 and froze me up. There's no easy way to get the full permissions for these files and put them all to my /usr/local/games/quake4/q4base folder ?? I appreciate your time Thanks for the reply

---

### Post by pay on 2006-12-16
For permissions```
sudo chown <username>:games /usr/local/games/quake4/q4base
sudo chmod -R 775 /usr/local/games/quake4/q4base
sudo gpasswd -a <username> games
```

---

### Post by eisle89 on 2006-12-17
eisle89@eisle89-desktop:~$ sudo chown -r eisle89:games /usr/local/games/quake4/q4base
Password:
chown: invalid option -- r
Try `chown --help' for more information.

---

### Post by eisle89 on 2006-12-17
eisle89@eisle89-desktop:~$ chmod 775 /usr/local/games/quake4/q4base
chmod: changing permissions of `/usr/local/games/quake4/q4base': Operation not permitted

---

### Post by eisle89 on 2006-12-17
This one worked OK 

eisle89@eisle89-desktop:~$ sudo gpasswd -a eisle89 games
Adding user eisle89 to group games

---

### Post by eisle89 on 2006-12-17
I got the chmod to work with a sudo

---

### Post by pay on 2006-12-17
Sorry my bad, try it how it is now.

---

### Post by Ryba on 2006-12-17
> **eisle89 said:**
> eisle89@eisle89-desktop:~$ sudo chown -r eisle89:games /usr/local/games/quake4/q4base
Password:
chown: invalid option -- r
Try `chown --help' for more information.
It is actually suppose to be with a capital R not lowercase. The -R option does a recursive change.

---

### Post by eisle89 on 2006-12-17
The capital R worked, thank you. So now how do I copy the files from my sda3 ( fat32) to my /usr/local/games/quake4/q4base folder. I can't copy them with a drag in my file browser. Oh, and in case you're wondering .... yeah, I'm a linux n00b ... ;) Thanks guys

---

### Post by eisle89 on 2006-12-17
OK, thanks alot I finally was able to drag the files over. Now lets see if this thing fires up. Thank you again for your time, with forum members like you this ubuntu will be the distro of choice.

---

### Post by eisle89 on 2006-12-17
ALRIGHT !!!! Fired up great !!!Thanks again  Now to search for how to make a desktop launcher for it

---

### Post by pay on 2006-12-17
To make a menu entry for it try ```
sudo nano /usr/share/applications/quake4.desktop
```then add this to the file```
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Name=Quake4
Comment=First Person Shooter
Exec=quake4
Icon=
Terminal=false
Type=Application
Categories=Application;Games
```

---

### Post by eisle89 on 2006-12-17
I tried it but can't find it now. should it be under Applications/Add/Remove ??  Tried to make a .png file from the .bmp in the quake4 folder but didn't have permission.

---

### Post by pay on 2006-12-17
It should be under applications, games. Try using```
sudo chown <username>:<username> /path/to/file.bmp
```to get permissions and when you change the format try```
sudo cp /path/to/image.png /path/to/quake4
```

---

### Post by eisle89 on 2006-12-17
It's not under my applications/games folder. I have all my games removed. With the icon, I'm opening up the q4icon.bmp in /usr/local/games/quake4. Then, using GIMP, I'm trying to save it as a .png file and I get a message that it can't allow it. pay, you seem to be the guy when it comes to Quake and I appreciate the time you're spending on this one, thanks

---

### Post by pay on 2006-12-18
Open up the file in Gimp, save it as a png in your home folder then copy it into the quake 4 base folder with```
sudo cp /home/<username>/q4icon.png /path/to/quake4/
```

---

### Post by eisle89 on 2006-12-18
Dammit pay, you're a genius Thank you. Now if I can just get these voices in Q4 working ...... ;)

---

### Post by pay on 2006-12-18
Try ```
quake 4 +set s_numberOfSpeakers 2 +set s_driver oss
```If that works change this```
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Name=Quake4
Comment=First Person Shooter
Exec=quake4
Icon=
Terminal=false
Type=Application
Categories=Application;Games
```to this```
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Name=Quake4
Comment=First Person Shooter
Exec=quake 4 +set s_numberOfSpeakers 2 +set s_driver oss
Icon=
Terminal=false
Type=Application
Categories=Application;Games
```

---

### Post by eisle89 on 2006-12-18
Well, I fired up Alacarte and made an entry for my Applications/Games folder so I have that there now. When I run the nano I can't seem to save it , I have multiple entries of it in my /usr/share/applications i.e. quake4.desktop.save,quake4.desktop.save1,quake4.desktop.save2

---

### Post by pay on 2006-12-18
Delete the entries that your not using.

---

### Post by eisle89 on 2006-12-20
Derrrr ........  Is that sudo del <path> ???

---

### Post by eisle89 on 2006-12-20
Nevermind pay, I did a sudo chown < path to file> and did sudo nautilus and deleted them. I'm sure there is an easier way but ...

---

