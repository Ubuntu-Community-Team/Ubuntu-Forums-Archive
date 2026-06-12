---
title: "WoW On Cedega - Help Please"
date: 2006-06-12
forum: Gaming &amp; Leisure
---

### Post by DiamondX on 2006-06-12
I am having problems with WoW+Cedega. After working on it for 3 days, I got it to actually load. My only problem is that it is unplayably slow. It goes at about 1FPS. Literally. The mouse is very smooth in DirectX mode, and just as slow as everything else in OpenGL.

I just got Cedega and am feeling very ripped off... their support sucks... The only way to get support is in their forums, and that is from other users... :mad: 

P.S. It doesnt slow down the rest of my computer, and I play in windows very smoothly with almost top settings.

---

### Post by =Kevin= on 2006-06-12
Try to run WoW.exe with the opengl synthax behind it, it will be much faster probably.

Like this:
cedega yourpathtotWow/Wow.exe -opengl

Try it and share your findings :)

---

### Post by DiamondX on 2006-06-12
[QUOTE==Kevin=]Try to run WoW.exe with the opengl synthax behind it, it will be much faster probably.

Like this:
cedega yourpathtotWow/Wow.exe -opengl

Try it and share your findings :)[/QUOTE]

I tried both -opengl and -d3d. Both are the same.

---

### Post by seth0x2b on 2006-06-12
Are other 3d/opengl applications running ok?!
There could be a problem with your display driver.
What does ```
glxinfo | grep direct
``` output?!

Cheers

---

### Post by sgtBiafra on 2006-06-13
I had a similar problem when I first started WoW under WINE. It turned out that I had not installed and properly configured GLX drivers for my nVidia card. 

Either run glxinfo as seth0x2b above suggests or even just look at the Driver section of your xorg.conf file (/etc/X11/xorg.conf). If it's using something like "nv" or "ati" you're running the unaccelerated driver.

Edit: Also, if you are using a nVidia card, look at the posts for Automatix. It's a GUI installer for many useful packages, among them nvidia-glx. It has the added benefit of setting up a working xorg.conf whereas simply installing the package from Synaptic doesn't always do so (usually requires a 'dpkg-reconfigure xserver-xorg').

---

### Post by Rizado on 2006-06-13
If I were you I'd use wine instead, I never could get wow working with cedega but it works great with wine and wow patches for wine.

---

### Post by DiamondX on 2006-06-13
I have an onboard video card by intel. I am using the i810 drivers.
When I do "glxinfo | grep direct" I get:
```
user@Ubuntu:~$ glxinfo | grep direct
direct rendering: Yes
```
I already canceled Cedega. What a ripoff!:-x

---

### Post by magomago on 2006-06-14
[QUOTE=DiamondX]I have an onboard video card by intel. I am using the i810 drivers.
When I do "glxinfo | grep direct" I get:
```
user@Ubuntu:~$ glxinfo | grep direct
direct rendering: Yes
```
I already canceled Cedega. What a ripoff!:-x[/QUOTE]

An i810 runs WOW at near full details?  I reallly find that hard to beleive lol!

---

### Post by thom_raindog on 2006-06-14
I used to run WoW on Cedega just fine for months now.... but after updating to Dapper I have a problem: When I move my mouse, my fps crash down to about 12fps and thats not playable. When I stop moving the mouse fps recover to my usual 40 within 2 seconds but this delay is very annoying.. any ideas?

---

### Post by eqisow on 2006-06-14
Honestly guys, I'd just give up Cedega and give WoW a shot on Wine. It works flawlessly for me and many others. (though not for all)

***DISCLAIMER: Intel integrated graphics are NOT going to run WoW well, especially in Wine/Cedega. Bottom line.***

Since you already have it installed in Cedega, you can create dynamic links to your Wine directory to avoid having to install again. Try the following and see how it goes:
```
wget http://thepiratecove.org/files/wine-0.9.15_wow_i386.deb
sudo apt-get --purge remove wine
sudo dpkg -i wine-0.9.15_wow_i386.deb
rm wine-0.9.15_wow_i386.deb
```

Now, run winecfg from the command line and go to the Drives tab. Hit the Autodetect button. Now, go to the Audio tab and make sure OSS Driver is checked and ALSA Driver in unchacked. Close winecfg. Now you will create symbolic links from or Cedega folder to a new Wine WoW folder as well as the Cedega mozcontrol.

```
ln -s '~/.cedega/World of Warcraft/c_drive/Program Files/World of Warcraft' '~/.wine/drive_c/Program Files/World of Warcraft'

ln -s '~/.transgaming_global/mozcontrol' '~/.wine/drive_c/Program Files/mozcontrol'
```

Now, you will backup your Wine registry and copy over the Cedega registry settings to Wine.

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

As of yesterday a hardware survey implemented by Blizzard broke WoW in Wine. This will fix that problem.

```
rm ~/.cedega/World of Warcraft/c_drive/Program Files/World of Warcraft/WDB/Survey.MPQ

chmod 555 '~/.cedega/World of Warcraft/c_drive/Program Files/World of Warcraft/WDB'
```

The following will stop the WoW background downloader, since it pops up in front of your screen and generally make your Wine WoW experience a headache.

```
mv ~/.cedega/World\ of\ Warcraft/c_drive/Program\ Files/World\ of\ Warcraft/BackgroundDownloader.exe ~/.cedega/World\ of\ Warcraft/c_drive/Program\ Files/World\ of\ Warcraft/BackgroundDownloader.exe_backup
```

Start WoW with the following, and use it to create a menu entry is desired.

```
wine 'C:/Program Files/World of Warcraft/WoW.exe'
```

Notes about WoW in Wine:

To change graphics settings you will need to start Wine in DirectX. Graphics may be messed up, but don't worry about it. It will go back to normal next time you run it normally. Run WoW in Direct X with the following.

```
wine 'C:/Program Files/World of Warcraft/WoW.exe' -d3d
```

Also, last time I tried, the WoW patcher doesn't always run corrently in Wine. However, patches are always available via direct download on various gaming sites (Google it). They are also generally available via BitTorrent.

If you have troubles, post back here or check the [World of Warcraft wiki]("https://wiki.ubuntu.com/WorldofWarcraft").

---

### Post by sgtBiafra on 2006-06-14
So it seems that our friend here is attempting to run this on an integrated Intel chipset (laptop perhaps?). By default, Ubuntu will use the i810 driver that ships with the included version of Xorg. It will apply this driver to anything from an i810 to the latest 950GMA (included in new Dell and MacBooks).

I would recommend investigating the universal Linux driver package that Intel offers on their site. It should support all of their recent chipsets but I'm not sure if it includes an XGL driver component.

A co-worker of mine has a similar problem on his laptop. If we manage to resolve it I'll post the fix here.

---

### Post by DiamondX on 2006-06-14
[QUOTE=magomago]An i810 runs WOW at near full details?  I reallly find that hard to beleive lol![/QUOTE]

Hehe... I know I sound like a troll here, but it is a 950. The i810 are the drivers for i810 and up, as sgtBiafra said. This is a laptop, and I seriously regret getting a better card. I get ~20 in starting areas with almost top setting in windows, which is smooth for me.

sgtBiafra: I didnt know they had a universal driver pack. Ill check it out.

P.S. I spent a week and a half trying to get it on wine, and gave up. Thats why I tried cedega. Its not worth it. Looking on their forums, more people didnt get it working than people who did. I guess Ill try wine again.

Edit: A quote from the drivers: " Intel(R) 945GM Chipset Support **(2D support only)**" I guess I need to wait. Anyone know if there are 3rd party, opensource drivers?

---

