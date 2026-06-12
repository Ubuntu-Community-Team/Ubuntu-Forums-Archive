---
title: "WOW - better in Wine or Cedega?"
date: 2006-08-10
forum: Gaming &amp; Leisure
---

### Post by Sammi on 2006-08-10
I want to ask people who have tried both to give me an honest answer to this question:

Does World of Warcraft run better in Wine or Cedega?

Don't want to make a poll, because I only want elaborated answers.
I don't really trust polls either.



I've personally only tried it in Cedega. It worked without much hassle and it runs pretty fluently, but only when I have have all my video settings set to low.
I have a rather large Dell Inspiron 9300 laptop with 1 gb RAM, 1,7 GHz Centrino, and a Geforce 6800 256 MB RAM, and think that I should be getting better performance.

I was wondering if it would be worth trying Wine, to get it running with higer settings.

---

### Post by simukas on 2006-08-10
i haven't tried WoW on wine, but i can say that it will be a pain i the ***. I can't get running event Diablo first or Warcraft II. I really thing that wine is kind off hopless now.

---

### Post by eqisow on 2006-08-10
Personally, I think it runs better in Wine. Since you already have it installed in Cedega, you can install it in Wine pretty easily by creating dynamic links to your Wine directory.
```
wget http://thepiratecove.org/files/wine-0.9.18_wow_i386.deb
sudo apt-get --purge remove wine
sudo dpkg -i wine-0.9.18_wow_i386.deb
rm wine-0.9.18_wow_i386.deb
```
Now, run winecfg from the command line and go to the Drives tab. Hit the Autodetect button. Now, go to the Audio tab and make sure OSS Driver is checked and ALSA Driver in unchecked. Close winecfg. Now you will create symbolic links from or Cedega folder to a new Wine WoW folder as well as the Cedega mozcontrol.
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
The following will stop the WoW background downloader, since it pops up in front of your screen and generally make your Wine WoW experience a headache.
```
mv ~/.cedega/World\ of\ Warcraft/c_drive/Program\ Files/World\ of\ Warcraft/BackgroundDownloader.exe ~/.cedega/World\ of\ Warcraft/c_drive/Program\ Files/World\ of\ Warcraft/BackgroundDownloader.exe_backup
```
Start WoW with the following, and use it to create a menu entry is desired.
```
wine 'C:/Program Files/World of Warcraft/WoW.exe'
```
For more general info on WoW in Wine check the [World of Warcraft wiki]("https://wiki.ubuntu.com/WorldofWarcraft").

---

### Post by Sammi on 2006-08-11
This:

```
ln -s '~/.cedega/World of Warcraft/c_drive/Program Files/World of Warcraft' '~/.wine/drive_c/Program Files/World of Warcraft'
ln -s '~/.transgaming_global/mozcontrol' '~/.wine/drive_c/Program Files/mozcontrol'
``` 
should be:

```
ln -s '~/.cedega/World of Warcraft/c_drive/Program Files/World of Warcraft' '~/.wine/drive_c/Program Files'
ln -s '~/.transgaming_global/mozcontrol' '~/.wine/drive_c/Program Files'
``` 
Everything else worked perfectly. Thanks!

It's quite nice how I'm able to use the same installation for both Wine and Cedega. Nice :cool:

And performance is up compared to Cedega, but still not on par with Wintendo. I'll get back to you with more detailed information on this.

---

### Post by patrick295767 on 2006-08-11
> **simukas said:**
> i haven't tried WoW on wine, but i can say that it will be a pain i the ***. I can't get running event Diablo first or Warcraft II. I really thing that wine is kind off hopless now.

Try this : 
linux gamers :
[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+INDEX+Wine+Games&back=HOWTO+Home](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+INDEX+Wine+Games&back=HOWTO+Home)
(I saw diablo first somewhere once ... maybe in artificial intelligence website)

Loki installers:
[http://liflg.org/?catid=7](http://liflg.org/?catid=7)
  
They are doing very great job; that's impressive and very easy to install games.

---

