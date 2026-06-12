---
title: "WoW Launcher"
date: 2007-02-21
forum: Gaming &amp; Leisure
---

### Post by denverreynolds on 2007-02-21
I got all of WoW working with the exception of using an icon to open it. I was just using a terminal. But then I thought I would do the same for the launcher and didnt think it would be a big deal. After entering the command wine Launcher.exe I get a popup window that says the program is trying to launch a web page and that I need to download a Gecko module. After installing, WoW locks up as soon as the splash screen for login comes up.

I looked over wtf.conf and xorg.conf and cant see any issues. Anyone ever have this pop up or any idea why its now locking up?

FYI,,no internet access because laptop isnt connected to LAN at work.

Thanks for any help!!

---

### Post by dtruesdale on 2007-02-21
Is it locking up when you have net access?

---

### Post by denverreynolds on 2007-02-21
No. It only hoses up when I try to run wine Wow.exe. It was fine before I downloaded the gecko package.

I had used my external hardrive to move WoW from my XP computer to my laptop. Thats why I dont have the launcher as an icon on my desktop.

Any idea's?

---

### Post by Sammi on 2007-02-21
launcher.exe is a launcher app for WoW, that also shows a few pieces of WoW related news, and you don't need to run it. Wine needs to download and install the gecko web engine(the same engine Firefox uses) to show the content in this app. I don't think that this works for everyone, but it works for me :D

Anyway you can very easily make an icon to launch WoW from. The folloeing is from the [community wiki on WoW/Wine]("https://help.ubuntu.com/community/WorldofWarcraft"): 

You can make a Gnome menu entry by doing the following:  

```
wget http://kde-files.org/CONTENT/content-files/41569-wow-icon-scalable.svg
sudo mv 41569-wow-icon-scalable.svg /usr/share/icons/
gksudo gedit /usr/share/applications/wow.desktop
```Add this to the text editor window, which should have appeared after the third command, change <username> in the Exec= line to your computer login username, and save:  

```
[Desktop Entry]
Encoding=UTF-8
Name=World of Warcraft
Name[hr]=World of Warcraft
Exec=wine /home/<username>/.wine/drive_c/Program\ Files/World\ of\ Warcraft/WoW.exe
Icon=41569-wow-icon-scalable.svg
Terminal=false
Type=Application
Categories=Application;Game;
StartupNotify=false
```*Note: Remember that you should also edit the Exec= line to reflect your WoW installation path, if you've installed to a special location.*

---

### Post by Praill on 2007-02-21
Ive noticed a similar problem.
For me, wine wont actually lock up, but it will never time-out when checking connectivity.
It seems WoW, or wine, or both, search for internet connectivity before the log in screen loads (bad programming either way since you cannot exit and have to wait) and wine never times-out but instead just keeps waiting.
Of course you can just ctrl+c, alt f4, alt tab and force close, or retart X (ctrl alt bckspace) but I dont think theres a solution to get wine to "time out".

Why would you want to run warcraft with no internet connectivity anyways? You will only be able to load the login screen and cinematics, and you can find the cinematics in the WoW folder anyways. It shouldnt matter if WoW can load without connectivity since the game is strictly online only.

---

### Post by Ferrat on 2007-02-22
The launcher is not useless! 

The launcher helps with updates, it updates the installer ect. 

weird you can get WoW to work but not the launcher, my launcher worked OOTB with wine 0.9.30

---

### Post by slayerboy on 2007-02-22
> **Ferrat said:**
> The launcher is not useless! 

The launcher helps with updates, it updates the installer ect. 


COMPLETELY untrue.  

When you launch wow with WoW.exe, it will start the program, the actual wow program does a check for updates.  When I used to play WoW, I never used the launcher and got updates.  The launcher is only used to display news that is easily viewed on the WoW website.

I actually stopped playing wow for a while because everything was breaking with the new Burning Crusade for me, and it didn't make any sense to continue paying.  Now that it's been a bit, I might try again.

---

### Post by denverreynolds on 2007-02-22
Reloaded Ubuntu and copied my WoW from external hard drive and it runs freaking FAST. I downloaded envy which auto installed the latest driver and I was getting 78+ FPS in Undercity.

I got smart and loaded all my saved bookmarks, WoW, MP3's, video's, and Ubuntu install disc onto my external HD. Now if I have to re-install it only takes about 2 hours to completely reconfig. Now I just need to get a backup scheduled so I dont have 153 updates to do when I reinstall.

Thanks so very much for all the help. Best, very best,,,I mean the very best forum help I have ever seen!

---

### Post by Skylara on 2007-05-22
> **slayerboy said:**
> COMPLETELY untrue.  

When you launch wow with WoW.exe, it will start the program, the actual wow program does a check for updates.  When I used to play WoW, I never used the launcher and got updates.  The launcher is only used to display news that is easily viewed on the WoW website.

Actually, the game itself will check for an update and download it - as you said - but you can't play while it downloads and it only downloads (the ENTIRE patch) on patch day.  

The Launcher checks for updates at every startup and can download patches in the background well in advance of patch day.  Plus it downloads while you play and when you log off so that the day of the actual patch release, you have all of the data and don't have to wait for hours for a large patch to download.

> **slayerboy said:**
> I actually stopped playing wow for a while because everything was breaking with the new Burning Crusade for me, and it didn't make any sense to continue paying.  Now that it's been a bit, I might try again.

I installed Ubuntu and WoW with no previous Ubuntu or Linux experience and got it all up and running the same day, so you should be fine.

Sorry to be resurrecting this thread after so long, but I would like some help on the Launcher as well.  I am using Edgy 6.10 and Wine 0.9.25 and can't get the Launcher to work.  The WoW How-To in these forums said to skip the Download DirectX message you get, but now I can't get the Launcher to work at all and it's patch day... and I am sitting here watching the downloader creep along in a 256MB patch download when it could have already been done.

Without upgrading to Feisty, is there any way to get my launcher to work?  Will Wine 0.9.30 as mentioned by another poster work with Edgy?

---

### Post by Ferrat on 2007-05-22
> **slayerboy said:**
> COMPLETELY untrue.  

When you launch wow with WoW.exe, it will start the program, the actual wow program does a check for updates.  When I used to play WoW, I never used the launcher and got updates.  The launcher is only used to display news that is easily viewed on the WoW website.

I actually stopped playing wow for a while because everything was breaking with the new Burning Crusade for me, and it didn't make any sense to continue paying.  Now that it's been a bit, I might try again.

The game check for game updates true but not for all the updates to the update program and that 's not updated as often but still updates come so sometimes you do need to run the launcher I can admit that I've only needed to do it maybe 5times during all the time I've played but still it is not useless

---

### Post by Sammi on 2007-05-22
> **Skylara said:**
> Sorry to be resurrecting this thread after so long, but I would like some help on the Launcher as well.  I am using Edgy 6.10 and Wine 0.9.25 and can't get the Launcher to work.  The WoW How-To in these forums said to skip the Download DirectX message you get, but now I can't get the Launcher to work at all and it's patch day... and I am sitting here watching the downloader creep along in a 256MB patch download when it could have already been done.

Without upgrading to Feisty, is there any way to get my launcher to work?  Will Wine 0.9.30 as mentioned by another poster work with Edgy?
Woops. That's old depreciated info as far as I know. I changed the howto to say yes instead.

> When the patch program, or the WoW Launcher starts, it will ask you about installing Mozilla ActiveX. Select "Yes". In doing this you will download a trimmed down version of the Gecko rendering engine (Firefox, Mozilla) which will respond to ActiveX calls, this means anytime a program tries to use HTML for a display, or similar, it will show. The launcher's news section and the changelog shown when applying a patch both use the rendering engine.

---

