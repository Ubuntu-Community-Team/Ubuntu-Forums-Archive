---
title: "Extract here shortcut in KDE for archive file ?"
date: 2009-01-01
forum: Desktop Environments
---

### Post by mansonthomas on 2009-01-01
Hi,

Is it possible to add on right click on an archive (zip, rar, tgz etc...) the same option you can have with winrar on windows ?  (Extract here, Extract in Folder 'Archive name' etc... ? 

Or is there another GUI that handle that ?

Thomas

---

### Post by skullmunky on 2009-01-01
This always used to be part of Konqueror in KDE3 by default.  I think it'll get added to KDE4 soon.  In the meantime you can add your own service menus (the menus you get when right clicking).  There's a long thread here that might help:

[http://kubuntuforums.net/forums/index.php?topic=3088743.0](http://kubuntuforums.net/forums/index.php?topic=3088743.0)

Here's what I have as a quick hack.  Save this code as a file called "myark_extract.desktop" and put it in your home directory, in .kde/share/kde4/services/ServiceMenus.

```

[Desktop Entry]
Type=Service
X-KDE-ServiceTypes=KonqPopupMenu/Plugin
MimeType=application/x-gzip;application/x-lha;application/x-tar;application/x-compressed-tar;application/x-bzip-compressed-tar;application/zip;application/x-bzip;application/x-tzo;application/x-lzop;application/x-rar;application/x-zoo;application/x-tarz;application/x-archiveapplication/x-java-archive;application/x-deb;application/x-zip-compressed;
Actions=extractHere

[Desktop Action extractHere]
Name=Extract Here
Exec=karchiver --extractarchdir %u
Icon=utilities-file-archiver

```

---

### Post by mansonthomas on 2009-01-01
Thanks skullmunky, I'll try that (after a good night of sleep(12*3600))!

Thomas

---

### Post by mansonthomas on 2009-01-02
I've added the file, installed karchiver,
when I click on extract here, the first time I had to configure karchiver, but the next time, it open then close without (apparently) doing nothing.

And when I click, open with karchiver, i get : 
karchiver window, plus a popup window asking for what to do : 

add this file to this archive or create archive stored as...

Is there anything to configure on karchiver ? 


Thomas

---

### Post by Skripka on 2009-01-02
> **skullmunky said:**
> This always used to be part of Konqueror in KDE3 by default.  I think it'll get added to KDE4 soon.  In the meantime you can add your own service menus (the menus you get when right clicking).  There's a long thread here that might help:

[http://kubuntuforums.net/forums/index.php?topic=3088743.0](http://kubuntuforums.net/forums/index.php?topic=3088743.0)

Here's what I have as a quick hack.  Save this code as a file called "myark_extract.desktop" and put it in your home directory, in .kde/share/kde4/services/ServiceMenus.



"Extract Here", along with several other extrating options are back in the context menu in KDE4.2 Beta2.

---

### Post by gjoellee on 2009-01-02
[COLOR=Red]it is in KDE 4.2 beta2 or higher[/COLOR]

---

### Post by mansonthomas on 2009-01-02
Well I'm on kubuntu 8.10...

```
thomas@daisybox:~/Desktop/$ sudo apt-cache show kde
Package: kde
Priority: optional
Section: universe/kde
Installed-Size: 40
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Qt/KDE Maintainers <debian-qt-kde@lists.debian.org>
Architecture: all
Source: meta-kde
Version: 5:48ubuntu1
Depends: kde-core (>= 5:48ubuntu1), kdeedu (>= 4:4.1.1), kdegames (>= 4:4.1.1), kdetoys (>= 4:4.1.1), kdeaccessibility (>= 4:4.1.1), kdeadmin (>= 4:4.1.1), kdeartwork (>= 4:4.1.1), kdegraphics (>= 4:4.1.1), kdemultimedia (>= 4:4.1.1), kdenetwork (>= 4:4.1.1), kdepim (>=4:4.1.1), kdeutils (>= 4:4.1.1), kdewebdev-kde4 (>= 4:4.1.1), kdeplasma-addons (>= 4:4.1.1)
Suggests: x-window-system-core, kde-l10n (>= 4:4.1.1)
Filename: pool/universe/m/meta-kde/kde_48ubuntu1_all.deb
Size: 8168
MD5sum: 37b5cb1829f3dbeae986c0d79935b8da
SHA1: 7b51195995a559bef8233b92d86a3d0640ea8380
SHA256: 3646bf8562f9f0d1a545d8a77474458aa973c60a63c492455c128aed8edcdb9d
Description: the K Desktop Environment official modules
 KDE (the K Desktop Environment) is a powerful Open Source graphical
 desktop environment for Unix workstations. It combines ease of use,
 contemporary functionality, and outstanding graphical design with the
 technological superiority of the Unix operating system.
 .
 This metapackage includes all the official modules released with KDE that
 are not specific to development. In addition to the core KDE modules, this
 includes multimedia, networking, personal information manager (PIM),
 graphics, education, games, web development, system administration tools,
 and other artwork and utilities.
Homepage: http://www.kde.org
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

```


When I remove the file in ServicesMenu, i loose the "Extract here" option on right click.

What apt-sources.list entry should I add to update to the last version of KDE ?

---

### Post by Skripka on 2009-01-02
> **mansonthomas said:**
> 

What apt-sources.list entry should I add to update to the last version of KDE ?

Read the following:

[http://www.kubuntu.org/news/kde-4.2-beta-2](http://www.kubuntu.org/news/kde-4.2-beta-2)

Know that Beta2 is just that and in using it you're playing with fire, and a RC won't happen for another ~2 weeks.  That said-for betaware I find it stable enough and more than usable for regular daily use...there are a few annoying bugs, that will go away when Ubuntu updates their Qt4 repos.

---

### Post by mansonthomas on 2009-01-02
Do you have an idea of the final release ? I can use command line for some time... in fact, I'm new to linux desktop, I use linux for servers for more that 8 years ;)

---

### Post by Skripka on 2009-01-02
> **mansonthomas said:**
> Do you have an idea of the final release ? I can use command line for some time... in fact, I'm new to linux desktop, I use linux for servers for more that 8 years ;)

Last I heard the KDE devs were aiming for 4.2 to be released near the end of January, the packaging for Beta2 for Ibex only took a few days to make it into the experimental repos so odds are the official release for Kubuntu will be February 1st or so.

They are only aiming for the 2 Betas, and 1 RC with a week of testing before tagging -so hopefully they can stick to that time table.

---

### Post by mansonthomas on 2009-01-02
Great, I'll wait then...

I'll try to figure out why I find ubuntu a bit slow with my config : 

I've a Core 2 Duo 6420, 4GB of high quality RAM, 2*250GB in RAID 1 (for linux, 2 raptors for windows), a Geforce 8800GTX (i've installed the nvidia drivers)

and for now, compared to windows XP, kubuntu really slower.
It's something i've to dig out... but there's a lot of things to discover at the sametime ;)

Although, if you have some tips, I'll be happy to read it!

Thanks,
Thomas.

---

### Post by Skripka on 2009-01-02
> **mansonthomas said:**
> Great, I'll wait then...

I'll try to figure out why I find ubuntu a bit slow with my config : 

I've a Core 2 Duo 6420, 4GB of high quality RAM, 2*250GB in RAID 1 (for linux, 2 raptors for windows), a Geforce 8800GTX (i've installed the nvidia drivers)

and for now, compared to windows XP, kubuntu really slower.
It's something i've to dig out... but there's a lot of things to discover at the sametime ;)

Although, if you have some tips, I'll be happy to read it!

Thanks,
Thomas.

What specifically is slower?

Graphics painting?
File transfer?
Boot?
App loading?
App multi-tasking?
.
.
.
?

---

### Post by mansonthomas on 2009-01-02
The general reponse time of the X server for displaying things, moving windows. 

I've forgot to mention that I work with a 24" screen, in 1920*1200... which is not uncommon nowdays, but may have an impact ;)

Also, I didn't find where I can set the mouse speed and acceleration as you can have in windows xp. With my large screen, the slow mouse speed doesn't help with the overall slow feeling.

It's slower than windows, but still usable (I now only use windows xp to play video games when I find some time to do so ;) ).

Is there any logfile to watch where I can find some hint to speed up things?

How can I know that my Nvidia drivers are correctly set up ?  In windows XP you can configure bunch of things that I don't know where to find on linux... 

(again, I didn't have time yet to search a lot, I manage a lot of server's which takes me a lot of search time)

My overall experience with KDE is great, I'm able to work, I find wonderfull application that perfectly replaces the windows app' I use before, some I didn't find yet a replacement. (I'll try codeweaver too for those)

the only weak point for now is the speed, which is not as good as Windows XP or Mac OSX.

Thomas

---

### Post by Skripka on 2009-01-02
> **mansonthomas said:**
> The general reponse time of the X server for displaying things, moving windows. 

I've forgot to mention that I work with a 24" screen, in 1920*1200... which is not uncommon nowdays, but may have an impact ;)

Also, I didn't find where I can set the mouse speed and acceleration as you can have in windows xp. With my large screen, the slow mouse speed doesn't help with the overall slow feeling.

It's slower than windows, but still usable (I now only use windows xp to play video games when I find some time to do so ;) ).

Is there any logfile to watch where I can find some hint to speed up things?

How can I know that my Nvidia drivers are correctly set up ?  In windows XP you can configure bunch of things that I don't know where to find on linux... 

(again, I didn't have time yet to search a lot, I manage a lot of server's which takes me a lot of search time)

My overall experience with KDE is great, I'm able to work, I find wonderfull application that perfectly replaces the windows app' I use before, some I didn't find yet a replacement. (I'll try codeweaver too for those)

the only weak point for now is the speed, which is not as good as Windows XP or Mac OSX.

Thomas

You say the Nvidia drivers are installed...just as a simple/easy check....they are activated (Under Hardware Jockey), yes?

Using a 24" panel shouldn't matter-my GTX260 is driving a 22" panel...and I currently have real fake digital snow flakes falling on my desktops (in lieu of the genuine article) in addition to roughly 1/3-1/2 of the effects activated, with my system not even thinking about it-much less slowing down any.

Mouse acceleration can be found under Sys Settings>Keyboard & Mouse>Mouse>Advanced Tab.

---

### Post by mansonthomas on 2009-01-02
Ok, Hardware Jockey, I've seen it when I installed the nvidia drivers.

Currently the 177 version has the green light. so should be good. (but no config option ?)

I've no 3D effects activated... Last time I tried : 

With openGL, i was only able to see the shadow of windows but not their content, so I had to start a TTY (CTRL+ALT+Fx), find which configuration file I should modify,modified it, and (CTRL+ALT+Backspace, old souvenir of my Redhat 8 installation years ago ;))

With XRender, It works, but I had some crashes or bad behaviour that made me disabled it...

I'll have to search on this... (and start some new threads ;)

Mouse Acceleration : Thx. In windows you have speed and acceleration, that why it disturbed me the first time I saw this screen. I've increased the acceleration, And now it's good ;)

Thanks Skripka ;)

Thomas

---

### Post by Skripka on 2009-01-02
> **mansonthomas said:**
> Ok, Hardware Jockey, I've seen it when I installed the nvidia drivers.

Currently the 177 version has the green light. so should be good. (but no config option ?)

Mouse Acceleration : Thx. In windows you have speed and acceleration, that why it disturbed me the first time I saw this screen. I've increased the acceleration, And now it's good ;)

Thanks Skripka ;)

Thomas

To configure the driver-you'll need to grab Nvidia-settings from your favorite package manager..or if you already have it, execute it with a graphical sudo command, i.e.

```

sudo apt-get install nvidia-settings

kdesudo nvidia-settings

```

Still is surprising that you have the driver running the show and a 8800GTX card is giving you slugishness. :confused:

---

### Post by mansonthomas on 2009-01-02
Thansk again, 

I've found some interesting thing in nvidia setting ;)

I use firefox a lot, and the memory fingerprint quickly exeed 1BG (I use multiple gmail interfaces (google apps [www.google.com/a]("http://www.google.com/a")), facebook, and loads of tabs for my research (such as, why can't I change the scaling governor of my CPU on my home ubuntu server...)

So, the slow impression maybe a bit from that too...


Ouch:  2h39 AM... time to go to bed... (moreover, I'm sick, I really need some sleep... to much things to learn on linux, you can spend youre whole life on it ;)

Thomas1

---

### Post by likes2skate on 2009-02-18
I do not care so much about the looks, I care a lot about the functionality.

I need right click compress.  It was not there when I installed kubuntu 8.10 a couple of days ago.  For me, that was a killer.  I wiped kubuntu 8.10 and instead installed kubuntu 8.04.

---

