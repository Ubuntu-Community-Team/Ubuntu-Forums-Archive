---
title: "new to ubuntu 9.04"
date: 2009-06-07
forum: General Help
---

### Post by chebbie on 2009-06-07
hey gus
i'm really new and wanted to take the leap onto linux for years, but didn't want to for the foremost reason of its technicality and difficulty to adapt and use this open source OS.
eventually, today, i've succeeded in installing it and i'm having my first problems in understanding how to use this os correctly and i've got some questions that i would like to ask you guys and i hope you can help me as best as you can with very little technicalities and programming explanation from you side since i ain't a programmer.

My questions:
(1) Do I have to use my Motherboard Installaion CD to install its respective components like i do after each installation of Microsoft XP for instance? (GIGABYTE 6 SUAD / S-SERIES CORE 2 DUO)

(2) Think it is not recognising my Video Card, do I have to install it again with the software provided by my video card. (G Force Driver CD NVIDIA 512MB)

(3) I inserted the CD but it is not working.  That is it does not automatically run the installation screen (how to permit such) and I browsed the folders but it couldn't open the executable files.

* please try to be very simple in your explanation.

(4) my movies were not playing and i had to install some plug ins that the software seached automatically. Nice.  But the movie LAGS it does not move at all, i've have to use the mouse to put the time bar for it to move.  So, it doesn't play at all and it does not have any sound.  I guess the soud is because I should install the software provided by my mother installation CD.

(5) Can I import my e-mails found in my respective folders on Microsoft Outlook onto Evolution E-mail.  The .pst files.  How?

(6) I write a lot of French whereby there are a lot of accents.  In Microsoft Office I can do such with the required codes, for e.g Alt+169.  In open office it ain't working.

(7) How can I lower the top bar whereby the applications, time, etc are found and bring it down with one single bar like in Microsoft WIndows?

(8)  Can I still use some Microsoft Software onto Ubuntu, for e.g continue using my Microsoft Outlook into here, Microsft Media Player, etc on Ubuntu.

I would appreciate if you could answer these issues to me asap since I'm very stuck right now into using this new OS.

Thanking you very much in advance.

Kind Regards.

---

### Post by ActiveFrost on 2009-06-07
Regarding motherboard drivers - forget about that CD .. all ( 99% ) drivers are already included and you don't need to install them again.
Video card - System -> Administration -> Hardware drivers ( in case if it's not already installed ).
Microsoft applications - you need to use Wine ( Google for it ).

Anyway, this will help you a lot : [https://help.ubuntu.com/community](https://help.ubuntu.com/community)

---

### Post by ikt on 2009-06-07
> **chebbie said:**
> i hope you can help me as best as you can

Your questions should all get answered in time, the main thing is to be patient and stick with it, a lot of people got used to windows over 5+ years of using it, then when they can't get ubuntu working in <24 hours run away claiming it's to hard to use.

I can only answer a few,

> **chebbie said:**
> 
My questions:
(1) Do I have to use my Motherboard Installaion CD to install its respective components like i do after each installation of Microsoft XP for instance? (GIGABYTE 6 SUAD / S-SERIES CORE 2 DUO)

The linux kernel has most drivers included with it, so no you shouldn't need to use a driver cd.

> **chebbie said:**
> 
(2) Think it is not recognising my Video Card, do I have to install it again with the software provided by my video card. (G Force Driver CD NVIDIA 512MB)

Head to:

System > Administration > Hardware Drivers and make sure your nvidia driver is enabled.

Can configure settings via

System > Preferences > Display

> **chebbie said:**
> 
(3) I inserted the CD but it is not working.  That is it does not automatically run the installation screen (how to permit such) and I browsed the folders but it couldn't open the executable files.

Programs written for windows do not work on linux, they might using wine but often they don't. Luckily for a majority of MS stuff there is an open source equivalent.



> **chebbie said:**
> 
(8)  Can I still use some Microsoft Software onto Ubuntu, for e.g continue using my Microsoft Outlook into here, Microsft Media Player, etc on Ubuntu.


You can try with a program called wine,

[http://www.winehq.org/](http://www.winehq.org/)

but generally running ms programs on linux is beside the point, there are most likely open source equivalents,

Microsoft Outlook = Evolution
Media Player = Totem/Audacious/Mplayer/Songbird etc
MSN Messenger = Pidgin

---

### Post by pbpersson on 2009-06-07
> **chebbie said:**
> 
(1) Do I have to use my Motherboard Installaion CD to install its respective components like i do after each installation of Microsoft XP for instance? (GIGABYTE 6 SUAD / S-SERIES CORE 2 DUO) 

You can never use a Windows CD on Linux.  Everything is completely different on Linux, you have entered a new world.

> **chebbie said:**
> 
(2) Think it is not recognising my Video Card, do I have to install it again with the software provided by my video card. (G Force Driver CD NVIDIA 512MB) 

Typically you can check System-->Administration-->Hardware Drivers  It might give you the option of a special driver for your graphics setup.

> **chebbie said:**
> 
(3) I inserted the CD but it is not working.  That is it does not automatically run the installation screen (how to permit such) and I browsed the folders but it couldn't open the executable files.


You cannot open .EXE files in Linux.  Those are Windows executable files.

> **chebbie said:**
> 
(4) my movies were not playing and i had to install some plug ins that the software seached automatically. Nice.  But the movie LAGS it does not move at all, i've have to use the mouse to put the time bar for it to move.  So, it doesn't play at all and it does not have any sound.  I guess the soud is because I should install the software provided by my mother installation CD.


What player are you using?  Try using VLC, it has always worked well for me.  You might need to use Synaptic Package Manager to find it and install it if you don't already have it.

> **chebbie said:**
> 
(5) Can I import my e-mails found in my respective folders on Microsoft Outlook onto Evolution E-mail.  The .pst files.  How?

Years ago I imported my .PST files into Thunderbird on a Windows machine and once they were in Thunderbird format I could transfer all my old Windows email to Linux.


> **chebbie said:**
> 
(7) How can I lower the top bar whereby the applications, time, etc are found and bring it down with one single bar like in Microsoft WIndows?


You can right-click on the panel, go to properties, and move it to the bottom.  There is a way to get only one panel, but keep in mind each panel is ONE line tall so all your open tasks need to fit down there.  My bottom panel is for menus, quick launch icons, weather, time, etc. and my top one is for open tasks.

> **chebbie said:**
> 
(8)  Can I still use some Microsoft Software onto Ubuntu, for e.g continue using my Microsoft Outlook into here, Microsft Media Player, etc on Ubuntu.

SOME Windows software you can run in Linux using Wine or Crossover.  I know nothing about such things, I have found applications that do everything in Linux that I used to do in Windows.

---

### Post by pbpersson on 2009-06-07
> **ikt said:**
> 

 generally running ms programs on linux is beside the point, there are most likely open source equivalents,

Microsoft Outlook = Evolution
Media Player = Totem/Audacious/Mplayer/Songbird etc
MSN Messenger = Pidgin

This web site might help: [ http://www.osalt.com/]("http://www.osalt.com/")

---

### Post by chebbie on 2009-06-07
Indeed.  I've been on Windows for 17 years.  It's only today that I've swtiched.  So you should understand my frustration right now in using Ubuntu.

So, no executable file won't run in Linux, that is the numerous software available won't run onto Linux.  GREAT! 

Now how to install software that ain't on the Install software thingee; that is i've got to download them.

For instance I downloaded Checkgmail, a similar program for Gmail Notifier, but I can't install it, or rather I don't know how to do it.

If I have to compress a file to send to someone; for instance in windows I used Winrar; that other guy could decompress it using winrar.  How about Linux.  I guess it has its own software.  Will that Guy using Windows will need the similar software too to decompress the file?

Can we install Adobe Photoshop, Dreamweaver, Illustrator, InDesign, etc on Ubuntu or we need a special version for Linux too?

---

### Post by chebbie on 2009-06-07
For a complete MPlayer installation you will need 	[sources]("http://www.mplayerhq.hu/design7/dload.html#source"), a set of 	[binary codecs]("http://www.mplayerhq.hu/design7/dload.html#binary_codecs"), and a 	[skin]("http://www.mplayerhq.hu/design7/dload.html#skins") if you want a graphical user interface. 
   	Quick compilation and installation instructions are contained in the 	[README]("http://www.mplayerhq.hu/DOCS/README"), the 	[installation section]("http://www.mplayerhq.hu/DOCS/HTML/en/install.html") 	of the documentation has more complete information. 



What the hell is that suppose to mean????????? man!!! it's more complicated to use Linux that I expected!!

---

### Post by ActiveFrost on 2009-06-07
You can create .zip and other type of archives with 7zip ( available in Synaptic ).
Usually, if you don't have a chance to install 7zip, use zip ( man zip ) ;)

---

### Post by 3rdalbum on 2009-06-07
> **chebbie said:**
> For a complete MPlayer installation you will need 	[sources]("http://www.mplayerhq.hu/design7/dload.html#source"), a set of 	[binary codecs]("http://www.mplayerhq.hu/design7/dload.html#binary_codecs"), and a 	[skin]("http://www.mplayerhq.hu/design7/dload.html#skins") if you want a graphical user interface. 
   	Quick compilation and installation instructions are contained in the 	[README]("http://www.mplayerhq.hu/DOCS/README"), the 	[installation section]("http://www.mplayerhq.hu/DOCS/HTML/en/install.html") 	of the documentation has more complete information. 

Yeah. Or, you could stop trawling the net for ready-to-compile software and just install Mplayer in three clicks from Synaptic Package Manager (System > Administration > Synaptic Package Manager).

Why do you want Mplayer? You already have Totem Movie Player. Totem should work with anything as long as you have a codec for it.

I'd also recommend going to [www.medibuntu.org](www.medibuntu.org) and adding the Medibuntu repository. It contains DVD playback plugins and codecs, all easily-installable from Synaptic Package Manager.

VLC is a better movie player than MPlayer, anyhow. You pretty much need VLC to play DVDs anyway. And yes, VLC is available in the Synaptic Package Manager (there's a pattern forming here...).

---

### Post by DeMus on 2009-06-07
> **chebbie said:**
> 
(1) Do I have to use my Motherboard Installaion CD to install its respective components like i do after each installation of Microsoft XP for instance? (GIGABYTE 6 SUAD / S-SERIES CORE 2 DUO)
No. Linux has everything on board already. Also this driver disk would probably only hold Windows drivers anyway.
> 
(2) Think it is not recognising my Video Card, do I have to install it again with the software provided by my video card. (G Force Driver CD NVIDIA 512MB)
Do you get the resolution you want?
Have a look in menu System - Administration - Hardware drivers and see if your card is listed here. If it is, click the Install button at the bottom to install it, and do a reboot.
> 
(3) I inserted the CD but it is not working.  That is it does not automatically run the installation screen (how to permit such) and I browsed the folders but it couldn't open the executable files.
Your driver cd probably only holds the windows driver
> 
(4) my movies were not playing and i had to install some plug ins that the software seached automatically. Nice.  But the movie LAGS it does not move at all, i've have to use the mouse to put the time bar for it to move.  So, it doesn't play at all and it does not have any sound.  I guess the sound is because I should install the software provided by my mother installation CD.
This is a driver and codec thing. Since the correct video-driver is not installed yet, you get this strange behavior when paying a video. No sound probably means you don't have the correct codec installed.
> 
(5) Can I import my e-mails found in my respective folders on Microsoft Outlook onto Evolution E-mail.  The .pst files.  How?
This seems to be possible nowadays but I have no experiences with that. Sorry
> 
(6) I write a lot of French whereby there are a lot of accents.  In Microsoft Office I can do such with the required codes, for e.g Alt+169.  In open office it ain't working.
Linux uses a slightly different codes system:
press ctrl-shift-u at the same time, let go of the keys then and press a number indicating the correct character. For example:
ctrl-shift-u 00e4 stands for ä
Open up Character map (menu Applications - Accessories - Character map, locate the character you want and look at the bottom of the window to see the correct code.
> 
(7) How can I lower the top bar whereby the applications, time, etc are found and bring it down with one single bar like in Microsoft WIndows?
Right-click the bottom panel and choose Delete this panel.
Then drag the top panel to the bottom. Right click it again and add to panel the items you want.
> 
(8)  Can I still use some Microsoft Software onto Ubuntu, for e.g continue using my Microsoft Outlook into here, Microsft Media Player, etc on Ubuntu.
Ubuntu knows a program called wine which is a layer between Linux and Windows. Install it through Synaptic (System - Administration - Synaptic package manager), type your password, search for wine, click the little square at the beginning of the line and select Mark for installation. Agree to any dependencies which might be there. Install through the Apply button in the button bar.
Now when opening a Windows program (like setup.exe) choose Wine to open it. Many windows programs work with Wine BUT NOT ALL.

---

### Post by 3rdalbum on 2009-06-07
> **chebbie said:**
> So, no executable file won't run in Linux, that is the numerous software available won't run onto Linux.  GREAT! 

Linux software doesn't run on Windows, either. Macintosh software doesn't run on Windows, nor vice-versa.

> Now how to install software that ain't on the Install software thingee; that is i've got to download them.

Try to find a third-party repository for them. If there are none, try finding a .deb package. If there are none, then you might need to compile some software. But most of the time you can find what you need in the repositories.

> For instance I downloaded Checkgmail, a similar program for Gmail Notifier, but I can't install it, or rather I don't know how to do it.

You mean, like these:

```

checkgmail - alternative Gmail Notifier for Linux via Atom feeds
gmail-notify - A Gmail Notifier
kcheckgmail - A Gmail notifier-like notifier for KDE
kgmailnotifier - Gmail notifier applet for KDE
mail-notification - mail notification in system tray
```

All available in Synaptic Package Manager. You might need to add the program to your Startup Applications or run them manually to get them to appear.

> If I have to compress a file to send to someone; for instance in windows I used Winrar; that other guy could decompress it using winrar.  How about Linux.  I guess it has its own software.  Will that Guy using Windows will need the similar software too to decompress the file?

File Roller can work with ZIP files, which are the defacto standard for compression on Windows. I'm not sure why Windows people seem to be using RAR these days, but in any case you can decompress these files in File Roller, if you install the "unrar" package from Synaptic.

> Can we install Adobe Photoshop, Dreamweaver, Illustrator, InDesign, etc on Ubuntu or we need a special version for Linux too?

Adobe has not made Linux versions, despite a huge number of requests.

Some versions of this software can be made to work on Wine, as long as they are legal copies. Unless you're a pro at Photoshop, you will find that The Gimp (preinstalled on Ubuntu) will service your needs quite nicely. It is **not a Photoshop clone** but it does include many of the same features, and a Photoshop user can adapt to The Gimp very quickly. I did.

In fact, some developers working for Adobe have been known to do their image editing in The Gimp...

---

### Post by DeMus on 2009-06-07
> **3rdalbum said:**
> In fact, some developers working for Adobe have been known to do their image editing in The Gimp...

Don't know if that is true but it won't surprise me at all.

---

### Post by ugm6hr on 2009-06-07
> **chebbie said:**
> So you should understand my frustration right now in using Ubuntu.

This is clearly a problem for you.

The key points to remember are:
1. Linux works differently to how you have previously used Windows.
2. Software is often not available cross-platform, and even if it is, requires an OS-specific version.
3. Installing software in Linux (Ubuntu) essentially requires a decent internet connection, and the ability to search using Synaptic (or Add/Remove).  Other methods are slightly more complex, but generally not required (I have only manually compiled on a couple of occasions).
4. People here are volunteer members of the Ubuntu community, and generally appreciate a bit of patience and courtesy; we are not paid technical support.

---

