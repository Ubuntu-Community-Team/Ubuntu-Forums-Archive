---
title: "WoW on Ubuntu 6.06"
date: 2006-11-16
forum: Gaming &amp; Leisure
---

### Post by Entase on 2006-11-16
Hey, I was wonderin how to get WoW to run on Wine (9.25, but i also have 9.6)

please go step-by-step and dont leave anyithing out, because I have no idea what im doing, and please dont redirect me to another thread, Ive looked at alot of them and cant make heads or tails of them, thanks


Entase

---

### Post by pay on 2006-11-16
You need to compile wine with special patches to use WoW. Firstly, add these repos to your /etc/apt/sources.list```
deb http://wine.budgetdedicated.com/apt edgy main
deb-src http://wine.budgetdedicated.com/apt edgy main
```Then download the dependencies```
sudo aptitude install build-essential
sudo apt-get build-dep wine
```Then download the source```
sudo apt-get source wine
```Then patch the source (Do you still need to patch the source anyone or are the patches merged into wine now because I can't find the updated patch)```
chown -R YOUR_USER_NAME:YOUR_USER_NAME wine*
cd wine*
wget http://slackbuilds.org/slackbuilds/misc/wine/wow_patch_nvidia_flicker_fix_0.9.25.diff.gz
tar zxvf wow_p*.diff
patch -p0 <  wow_patch_nvidia_flicker_fix_0.9.25.diff
cd
sudo apt-get --build-source wine
```
and then install it```
sudo dpkg -i wine/wine*.deb
```

Now to configure wine. I use this script
```
wget http://sidenet.ddo.jp/winetips/files/wine-config-sidenet-1.9.2-test2.tgz
tar zxvf wine-config-sidenet-1.9.2-test2.tgz
cd wine-config-sidenet
sh setup
```

Now to get the needed .dlls
[http://www.dll-files.com/dllindex/dll-files.shtml?msvcp60](http://www.dll-files.com/dllindex/dll-files.shtml?msvcp60)
[http://www.dll-files.com/dllindex/dll-files.shtml?msvcp60](http://www.dll-files.com/dllindex/dll-files.shtml?msvcp60)
Download and copy to .wine/drive_c/windows/system32 (its a hidden folder)

Then copy the cd to the computer (because some have had trouble reading the files)
```
cp -R /media/cdrom0/* WoWinstall/ # Assuming that /media/cdrom0 is  your cdrom
cp -g /media/cdrom0/Installer\ Tome\ 2.mpq WoWinstall/
```Repeat for each cd. Now to install```
wine WoWinstall/setup.exe -opengl
```
To run the game run wine /path/to/where/you/installed/WoW/wow.exe -opengl

---

