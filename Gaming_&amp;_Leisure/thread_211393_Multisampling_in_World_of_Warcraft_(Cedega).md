---
title: "Multisampling in World of Warcraft (Cedega)"
date: 2006-07-08
forum: Gaming &amp; Leisure
---

### Post by ImaMadGoat on 2006-07-08
Hello all,

I've done quite a bit of searching on this subject and I'm surprised that I'm not finding many answers. Before I explain, here is my system.

Intel P4 2.8ghz
1024 MB RAM
Dual Booting Windows and Dapper 6.06 on separate 40GB hard drives
Nvidia 6600GT 128MB AGP
SB Audigy Sound Card

So the main thing that keeps me from using Linux exclusively is WoW. I've had success running WoW in Cedega through Gnome (KDE and Xubuntu don't allow a playable frame rate. I don't know why, but it runs in gnome so I'm happy with that). I've setup all my addons and video settings. It plays pretty well except for one thing....Multisampling.

Is there a reason why I can only get a x1 MSing rate? Under windows I was able to get x4 in 24bit depth with an good framerate (35+) (25+ in Lagforge). 

I know it's somewhat silly, but I've heard others saying that WoW runs better for them in Linux than it did under Windows. As far as loading times  are concerned, I'm sold already. But I'd really like to smooth out the edges like I can in Windows. 

One more thing...I've gone into Nvida settings and enabled my antialiasing but I'm not seeing a game effect. Is there a way to enable World of Warcraft-specific settings?

Other than these issues...I am LOVING Ubuntu! /cheers

---

### Post by eqisow on 2006-07-08
I'm not sure about the multisampling, to be honest. One solution you could try is just to set the multisampling as low as it will go, and run in a higher resolution. You should be able to run *at least* 1024 with that system. The higher the res, the less jaggies you will see, despite the low multisampling.

Another option is to give Wine a try. For me it works just as well or better than Cedega, and is also free. Since you already have WoW installed in Cedega, I will write out special instructions so you don't have to waste HD space reinstalling WoW.

Begin by installing the latest version of Wine pre-patched for WoW.
```
wget http://thepiratecove.org/files/wine-0.9.16_wow_i386.deb
sudo apt-get --purge remove wine
sudo dpkg -i wine-0.9.16_wow_i386.deb
rm wine-0.9.16_wow_i386.deb
```
Now, run winecfg from the command line and go to the Drives tab. Hit the Autodetect button. Now, go to the Audio tab and make sure OSS Driver is checked and ALSA Driver in unchecked. Close winecfg. Now you will create symbolic links from or Cedega folder to a new Wine WoW folder as well as the Cedega mozcontrol.
```
ln -s '~/.cedega/World of Warcraft/c_drive/Program Files/World of Warcraft' '~/.wine/drive_c/Program Files/World of Warcraft'

ln -s '~/.transgaming_global/mozcontrol' '~/.wine/drive_c/Program Files/mozcontrol'
```
Now, you will copy the Cedega fonts to your Wine directory, backup your Wine registry, and copy over the Cedega registry settings to Wine.
```
cp ~/.transgaming_global/Fonts/* ~/.wine/drive_c/windows/fonts
cp ~/.wine/user.reg ~/.wine/user.reg_backup
cp ~/.wine/system.reg ~/.wine/system.reg_backup
cp ~/.wine/userdef.reg ~/.wine/userdef.reg_backup
cp ~/.cedega/World\ of\ Warcraft/*.reg ~/.wine/
```
The following will set the WoW config files to the appropriate settings to run in Wine.
```
wget http://thepiratecove.org/files/Config.WTF
mv Config.WTF ~/.cedega/World\ of\ Warcraft/c_drive/Program\ Files/World\ of\ Warcraft/WTF/Config.wtf
```
If Wine crashes when you try to log in, the following should fix the issue.
```
rm ~/.cedega/World of Warcraft/c_drive/Program Files/World of Warcraft/WDB/Survey.MPQ
chmod 555 '~/.cedega/World of Warcraft/c_drive/Program Files/World of Warcraft/WDB'
```
The following will stop the WoW background downloader, since it sometimes pops up on top of WoW screen and is generally annoying. This step is optional.
```
mv ~/.cedega/World\ of\ Warcraft/c_drive/Program\ Files/World\ of\ Warcraft/BackgroundDownloader.exe ~/.cedega/World\ of\ Warcraft/c_drive/Program\ Files/World\ of\ Warcraft/BackgroundDownloader.exe_backup
```
To start WoW from the command line, use the following.
```
wine 'C:/Program Files/World of Warcraft/WoW.exe' -opengl
```
If you want to create a menu entry for Wine, do this:
```
sudo cp ~/.cedega/World\ of\ Warcraft/icons/World\ of\ Warcraft.png /usr/share/pixmaps/WoW.png

sudo gedit /usr/share/applications/wow.desktop
```
Insert the following lines into the new file and save it:
```
[Desktop Entry]
Name=World of Warcraft
Comment=World of Warcraft in Wine
Exec=wine 'C:/Program Files/World of Warcraft/WoW.exe' -opengl
Icon=/usr/share/pixmaps/WoW.png
Terminal=false
Type=Application
Categories=Application;Game;
```
Notes about WoW in Wine:

To change graphics settings you will need to start Wine in DirectX mode. Graphics may be messed up, but don't worry about it. It will go back to normal next time you run it with OpenGL. Run WoW in DirectX with the following.

```
wine 'C:/Program Files/World of Warcraft/WoW.exe' -d3d
```

The WoW patcher seems to now be working with Wine, but patches are always available via direct download on various gaming sites as well as BitTorrent if it starts acting up again.

If you have troubles, post back here or check the [World of Warcraft wiki]("https://help.ubuntu.com/community/WorldofWarcraft").

---

### Post by ImaMadGoat on 2006-07-08
Ok....doing great so far.

I'm able to get 24bit 16bit depth x4 multisample running it through wine with the directions you gave me.

I have only one issue left to deal with which is refresh rate. WoW settings are a refresh rate of 75htz. My screen is only capable of 60htz. It's a CMV 19" LCD. 

I have set my resoluton to 1280x1024, but because the RR is 75, it's showing up at what appears to be 800x600. How can I chage my refresh rate? Ingame video settings don't give me the option, and I don't see a setting in the config file.

Other than that....you're nailing this one and I'm very happy

---

### Post by eqisow on 2006-07-08
That's odd, WoW has always detected my refresh rate fine. But at any rate, you can change your refresh rate directly in your Config.wtf. First, open your config file.

```
gedit ~/.wine/drive_c/Program\ Files/World\ of\ Warcraft/WTF/Config.wtf
```

Now look for the following line:

```
SET gxRefresh "75"
```

If you find it, change it to whatever you want your refresh rate to be. If you don't find it, add the line and change 75 to the desired refresh rate.

---

