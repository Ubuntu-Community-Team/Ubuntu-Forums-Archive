---
title: "WoW prob"
date: 2006-12-30
forum: Gaming &amp; Leisure
---

### Post by dal2k5 on 2006-12-30
Hi i hve installed WoW on my system, but when i double click on it, it go's to tht screen tht says play and stuff like tht when i click it the moniter shows a message saying input signal out of range change settings to 1280x1024 and 60hz. Wtf

---

### Post by dal2k5 on 2006-12-30
Bump

---

### Post by Ferrat on 2006-12-30
more information please :) 

Wine or Cedega? 
What version? 
how did you install it?
how did you install grafic drivers ? 
are you 100% that they are working?
Have you tried editing the WTF config file to get 1280x1024 resolution?

---

### Post by dal2k5 on 2006-12-30
wine
i downloaded it and installed it via wine
i downloaded the drivers from ati's site
ummm
no

---

### Post by hikaricore on 2006-12-30
....even though you're offering very little information which is vital to helping you solve your problem, I'm going to throw a few useful bits of info at you.

ok you're using wine... saying you intalled it from wine doesn't help

What version of wine did you install?
Did you install the version or wine in the ubuntu package repository,
Did you download with the most recent dapper package,  [Which is located here.]("http://wine.budgetdedicated.com/archive/index.html")
Or did you download and compile the application from source?

Have you run **winecfg** to setup wine for the first time?  
Have you checked the [Wine Application Database's World of Warcraft page]("http://http://appdb.winehq.org/appview.php?iAppId=1922") for tips and useful information for modifying your Config.wtf file incase there would be a simple solution you might have overlooked? (Such as possibly _MANUALLY_ typing in the proper resolution.)

What type/version of the driver package did you install?
Was it a debian/ubuntu package file or a binary installer?
Did it install sucessfully or was there an error output?
Did you restart your computer or at the very least your X session before attempting to continue after installing drivers?

Have you run from a terminal:

```
glxinfo | grep rendering
```

As suggested by nearly every driver installation HOWTO listed on these forums?

Does this return: **direct rendering: Yes**

If not you will need to either configure or troubleshoot your driver setup.

Is your xorg.conf file set to 24bit colour?

Did you follow the instructions listed in EVERY SINGLE WoW linux howto by starting it with the "*--opengl*" flag?

Provide clear and precise information if you would like people to assist you, many members of this community do this out of the good of their own hearts, and get nothing in return for it but your success and happiness as a member of this community.

Good luck,

--Aaron

---

### Post by dal2k5 on 2006-12-30
> **hikaricore said:**
> ....even though you're offering very little information which is vital to helping you solve your problem, I'm going to throw a few useful bits of info at you.

ok you're using wine... saying you intalled it from wine doesn't help

What version of wine did you install?
Did you install the version or wine in the ubuntu package repository,
Did you download with the most recent dapper package,  [Which is located here.]("http://wine.budgetdedicated.com/archive/index.html")
Or did you download and compile the application from source?

Have you run **winecfg** to setup wine for the first time?  
Have you checked the [Wine Application Database's World of Warcraft page]("http://http://appdb.winehq.org/appview.php?iAppId=1922") for tips and useful information for modifying your Config.wtf file incase there would be a simple solution you might have overlooked? (Such as possibly _MANUALLY_ typing in the proper resolution.)

What type/version of the driver package did you install?
Was it a debian/ubuntu package file or a binary installer?
Did it install sucessfully or was there an error output?
Did you restart your computer or at the very least your X session before attempting to continue after installing drivers?

Have you run from a terminal:

```
glxinfo | grep rendering
```

As suggested by nearly every driver installation HOWTO listed on these forums?

Does this return: **direct rendering: Yes**

If not you will need to either configure or troubleshoot your driver setup.

Is your xorg.conf file set to 24bit colour?

Did you follow the instructions listed in EVERY SINGLE WoW linux howto by starting it with the "*--opengl*" flag?

Provide clear and precise information if you would like people to assist you, many members of this community do this out of the good of their own hearts, and get nothing in return for it but your success and happiness as a member of this community.

Good luck,

--Aaron


kk i typed glxinfo | grep rendering into the terminal and i got > Xlib:  extension "XFree86-DRI" missing on display direct rendering: no":0.0".
wtf :-k 
i got the latest version of wine off winehq's website yes i hve run winecfg
i did succsefully install WoW with no errors at all, when i installed the ati drivers i restarted the comp. i got the driver from here [http://ati.amd.com/support/drivers/linux/linux-firegl.html](http://ati.amd.com/support/drivers/linux/linux-firegl.html) and i downloaded the ati driver installer

---

### Post by hikaricore on 2006-12-30
It appears that your drivers aren't properly configured.  You may want to search around the forums for info on your specific card.  It may be as easy as modifying your xorg.conf file and restarting X.  But ati cards are known to be problematic from time to time.

I'm not an expert on ATI drivers but hopefully someone can help you out with the issue if you can't find anything on the forums for a solution.

Good luck,

--Aaron

---

### Post by dal2k5 on 2006-12-30
> **hikaricore said:**
> It appears that your drivers aren't properly configured.  You may want to search around the forums for info on your specific card.  It may be as easy as modifying your xorg.conf file and restarting X.  But ati cards are known to be problematic from time to time.

I'm not an expert on ATI drivers but hopefully someone can help you out with the issue if you can't find anything on the forums for a solution.

Good luck,

--Aaron

thnx man!!!!!!!!!!:D :D :D :D

---

### Post by Sammi on 2006-12-31
These are a few guides on installing ATI drivers that I have found. Hopefully one will work for you.
 
I recomend you try this guide first:
[[COLOR=#bd5900]http://wiki.cchtml.com/index.php/Ubu...allation_Guide[/COLOR]]("http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide")

then:
[[COLOR=#bd5900]http://www.ubuntuforums.org/showthre...ighlight=fglrx[/COLOR]]("http://www.ubuntuforums.org/showthread.php?t=305665&highlight=fglrx")

Automatix Bleeder also has an option for installing ATI drivers automaticly, but it may not be stable:
[[COLOR=#bd5900]http://www.getautomatix.com[/COLOR]]("http://www.getautomatix.com/wiki/index.php?title=Installation#Installing_Automatix2_Bleeder_.28only_on_Ubuntu_6.10_i386_as_of_now.29")

---

### Post by dal2k5 on 2006-12-31
> **Sammi said:**
> These are a few guides on installing ATI drivers that I have found. Hopefully one will work for you.
 
I recomend you try this guide first:
[[COLOR=#bd5900]http://wiki.cchtml.com/index.php/Ubu...allation_Guide[/COLOR]]("http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide")

then:
[[COLOR=#bd5900]http://www.ubuntuforums.org/showthre...ighlight=fglrx[/COLOR]]("http://www.ubuntuforums.org/showthread.php?t=305665&highlight=fglrx")

Automatix Bleeder also has an option for installing ATI drivers automaticly, but it may not be stable:
[[COLOR=#bd5900]http://www.getautomatix.com[/COLOR]]("http://www.getautomatix.com/wiki/index.php?title=Installation#Installing_Automatix2_Bleeder_.28only_on_Ubuntu_6.10_i386_as_of_now.29")

thnx man!!!!

---

### Post by dal2k5 on 2006-12-31
kk the grafix card installed succesfully thnx to this guide [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)
but when i launch WoW the sound kinda skips....and when i get to the login screen it crashes....plz some1 help

---

### Post by Sammi on 2006-12-31
Have you configured Wine to use OSS instead of ALSA for sound?

You can do this by running the command "winecfg". Only OSS should be enabled under "audio" or something similar.

---

### Post by dal2k5 on 2006-12-31
1 more question when i run WoW i get a message tht says 

Hardware Changed. Reload defult settings?
yes or no?
wat should i choose?

---

### Post by Sammi on 2006-12-31
I'm not really sure, but I think WoW will overwrite you config.wtf file with default values, if you select yes, and thus overwrite any manual changes you have made to it. That's why I always select "NO".

Is everything working now?

---

### Post by dal2k5 on 2006-12-31
no...when i get to the login screen WoW crashes....

---

### Post by hikaricore on 2006-12-31
and you're running it with the opengl flag?

```
wine ~/.wine/drive_c/Program\ Files/World\ of\ Warcraft/WoW.exe **--opengl**
```

This assumes your WoW installation is in the standard path.

I'm not sure how well your particular card handles opengl, so that may be an issue, just a guess.

Good luck,

--Aaron

---

### Post by Sammi on 2006-12-31
It doesn't seem like you've seen our community ubuntu-wow-wine howto: [help.ubuntu.com/community/WorldofWarcraft]("http://www.ubuntuforums.org/help.ubuntu.com/community/WorldofWarcraft")

The common problems with running wow under wine on ubuntu are all solved in the steps listed there.

---

