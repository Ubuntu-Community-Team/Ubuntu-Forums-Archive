---
title: "Uninstall Steam in Wine"
date: 2016-01-06
forum: Gaming &amp; Leisure
---

### Post by heroquestelf on 2016-01-06
Okay, so I heard that Wine had a major upgrade, and I was hoping to be able to run an old Windows game that I had purchased through Steam, so I installed the Windows version of Steam through Wine. As it turns out, the new version of Wine can't handle the game any better than the old version. (Space Empires IV, if you're curious.)

SO, I figured out how to uninstall SEIV, but now I want to completely remove the Windows version of Steam, as I don't need it. It's just taking up space on my hard drive. My concern is this: when I launch the Wine uninstaller, Steam does not show up. The only things that show up are Starcraft II, Wine Gecko and Adobe Photoshop.  I don't want to completely purge my Wine folders, as I that'll purge Starcraft II and an older version of Adobe Photoshop... and that Photoshop was a straight up pain in the **** to get working. I do NOT want to have to reinstall it now that I got it working right. 

The other bug in the system is that I have the Linux version of Steam also installed on my system and I am worried that if I start pell-nell deleting files associated with Steam I'm going to somehow screw that up as well. Can somebody walk me through this?

---

### Post by MikeCyber on 2016-01-07
Should be as easy as deleting all steam folders.
Do something alike in your .wine directory:
find . -name "*team*" to search.

wine apps don't interfere at all. have a look at playonlinux as that's easier.

---

### Post by heroquestelf on 2016-01-07
Okay, I went into .local/share/wineprefixes and deleted the "steam" folder, but now when I enter a search the old app still shows up. It won't launch, obviously, since the files supporting it are all gone, but it still shows up. How do I delete it?

---

### Post by MikeCyber on 2016-01-07
Anything from wine is in the hidden directory .wine. Usually this in your home:
ls -la
should show that folder. Now in that directory delete all folders with steam. Anything outside of .wine is from your ubuntu steam.
whereis steam
should give a hint.

---

### Post by heroquestelf on 2016-01-07
Okay, here's what I have done so far. First I did a > sudo nautilus command and did a search for "Steam". I deleted anything under "Wine", "Wineapps" or "Winepreinstall". This left me with several files in a home/.local/share/steam folder and a home/.steam folder. I also had some files in my usr/local directory that were also associated with Steam. I did not delete any of those. I then ran the Unity tweak tool and had it to delete the history, and the icon for the Windows version of Steam still shows up if you run a search for Steam. I have also rebooted multiple times during this process.

Granted, it's nothing more than an annoyance at this point, but it is an annoyance. Any suggestions?

---

### Post by MikeCyber on 2016-01-08
I said the hidden directory .wine
It's easy to make a copy of that directory before installing new apps or make backups.

PS: Never use sudo unless you absolutely need to.

---

### Post by heroquestelf on 2016-01-08
You misread what I was saying. 

I ran the *sudo nautilus* command because I wanted full access to my system. I wanted it to search hidden files and all, and I wanted to be able to delete things in system folders if they were associated with the Windows version of Steam.

I then did a COMPLETE hard drive search. I found "Steam" files in the following directories:

home/.wine
home/winepreinstall
home/wineapps
home/.steam
home/.local/share/steam
usr/local (as well as some subdirectories of usr/local)
as well as some icons in the usr/share/applications folder.

I found things in the "home/.wine" folder, the "home/wineapps" folder, and the "home/wineprinstall" folder. I made the assumption that all of THESE files were associated with the Windows version of Steam I installed. I deleted all of that information. I also deleted the icon file in the usr/share/applications folder for the Windows version of Steam, leaving the Linux icon.

I did NOT delete the Steam files I found in the "home/.steam" folder, or any of the Steam files in the "home/.local/share/steam" folder or my "usr/local" folder. I made the assumption that all of THESE files were associated with the Linux version of Steam I installed.

AH-HA!!!

Nevermind!! I finally found the culprit!!

Thanks for all your help!!

---

### Post by QIII on 2016-01-08
Hello!

Could you please share the solution so that others may learn?

Thanks.

---

### Post by heroquestelf on 2016-01-08
The directory I missed was "home/.local/share/wine/steam"

Once that directory was deleted the icon went bye-bye.

---

