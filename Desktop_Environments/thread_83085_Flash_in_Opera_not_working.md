---
title: "Flash in Opera not working"
date: 2005-10-27
forum: Desktop Environments
---

### Post by SadaraX on 2005-10-27
I am having trouble using flash in the Opera version 8.50 web browser under Kubuntu 5.10. Specifically, websites like:

[http://homestarrunner.com/sbemail.html](http://homestarrunner.com/sbemail.html)

Do not work for me. In fact, nothing seems to show up at all. I have tested Opera 8.50 on my Debian Mepis system and it plays just fine. I installed the deb file of Opera from the opera.com website by selecting the Ubuntu Breezy 5.10. 

Has anyone else had the problem of flash not working well? Any solutions?

---

### Post by Xian on 2005-10-28
Try installing the packages below then reload Opera. It should place the flash plug-in in the /usr/lib/mozilla/plugins directory, which will then be recognized by Opera.

```
$ sudo apt-get install flashplayer-mozilla flashplugin-nonfree
```

---

### Post by Moonbuzz on 2005-10-28
I downloaded the plugin from Macromedia, it explicitely allows you to install it on Opera folder. 
Opera also has the FireFox folder in its Plugin path.

---

### Post by SadaraX on 2005-10-28
[QUOTE=Moonbuzz]I downloaded the plugin from Macromedia, it explicitely allows you to install it on Opera folder. 
Opera also has the FireFox folder in its Plugin path.[/QUOTE]

I tried it before but that did not help. I will try that again to see if messed something up.

---

### Post by SadaraX on 2005-10-28
[QUOTE=Xian]Try installing the packages below then reload Opera. It should place the flash plug-in in the /usr/lib/mozilla/plugins directory, which will then be recognized by Opera.

```
$ sudo apt-get install flashplayer-mozilla flashplugin-nonfree
```[/QUOTE]

Thanks, I will give this a try.

---

### Post by SadaraX on 2005-10-28
Well, I tried:

```
$ sudo apt-get install flashplayer-mozilla flashplugin-nonfree
```

I tried this and it did no good unfortunately. I even went to the place where the *.tar.gz file downloaded from apt, and then installed the files from that.

It made no difference. No flash in opera. Just for information:

```
/usr/lib/opera/plugins # ls -l
-rwxr-xr-x  1 root root     856 2005-10-28 17:49 flashplayer.xpt
-rwxr-xr-x  1 root root 2096844 2005-10-28 17:49 libflashplayer.so
-rw-r--r--  1 root root   66528 2005-09-16 03:14 libnpp.so
-rwxr-xr-x  1 root root   77520 2005-09-16 03:14 operamotifwrapper-3
-rwxr-xr-x  1 root root    6944 2005-09-16 03:14 operaplugincleaner
```

---

### Post by Xian on 2005-10-28
Check to see if the plugin is listed in your preferences menu. 
From the main menu in Opera:

Tools > Preferences > Advanced > Plugin Options

Look anything like this?:

[img]http://img.photobucket.com/albums/v469/camplear/forums/OperaPlugs.png[/img]

---

### Post by SadaraX on 2005-10-29
I do not have a window like that. When I go to:

Tools -> Advanced -> Plug-ins, it opens a screen with this text:

> 
Shockwave Flash	
application/futuresplash	spl	
application/x-shockwave-flash	swf	
/usr/lib/opera/plugins/libflashplayer.so 	
  	
NS4PluginProxy	
application/x-opera-nsplugin	-	
/usr/lib/opera/plugins/libnpp.so 	
  	
Shockwave Flash	
application/futuresplash	spl	
application/x-shockwave-flash	swf	
/home/clifton/.mozilla/plugins/libflashplayer.so 	
  	
Shockwave Flash	
application/futuresplash	spl	
application/x-shockwave-flash	swf	
/usr/lib/mozilla/plugins/libflashplayer.so 	
  	
Shockwave Flash	
application/futuresplash	spl	
application/x-shockwave-flash	swf	
/usr/lib/netscape/plugins-libc6/libflashplayer.so


Going to the prefences menu, I messed around in the "Downloads" section with files that have the .swf extention, but that did not really help. I had all four of those options as plugins to open them with, but no option I checked made any difference.

---

### Post by Xian on 2005-10-29
[QUOTE=SadaraX]I do not have a window like that. When I go to:

Tools -> Advanced -> Plug-ins, it opens a screen with this text:[/QUOTE]
Sorry, let's try that path again:

Tools > Preferences > Advanced > Content > Plug-in Options

---

### Post by SmellyLlama on 2005-10-29
When I start opera I get an error message which states that it can't find motif, and that it needs motif to get the plugins working. At the bottom it stands
Please install motif.

I can't post a screen shot, because I told it not to show up again.

---

### Post by Xian on 2005-10-29
[QUOTE=SmellyLlama]When I start opera I get an error message which states that it can't find motif, and that it needs motif to get the plugins working. At the bottom it stands
Please install motif.[/QUOTE]

Try installing the [lesstif2](http://packages.ubuntu.com/breezy/libs/lesstif2) package.

```
$ sudo apt-get install lesstif2
```

---

### Post by MetalFatigue on 2005-10-30
[QUOTE=Xian]Try installing the [lesstif2](http://packages.ubuntu.com/breezy/libs/lesstif2) package.

```
$ sudo apt-get install lesstif2
```[/QUOTE]

I have the same problem with the plugins. It shows that message that I can't use plugins. I have motif3 and lesstif2 installed too.

By the way  motif3 can be found at [http://packages.ubuntu.com/breezy/libs/libmotif3](http://packages.ubuntu.com/breezy/libs/libmotif3)

I read in a opera forum that motif3 needs to enable multiverse repo. If someone could help a noob on how to do this, would appreciate ;)

---

### Post by Xian on 2005-10-30
[QUOTE=MetalFatigue]I have the same problem with the plugins. It shows that message that I can't use plugins. I have motif3 and lesstif2 installed too.[/quote]
Install this version of Opera: [opera_8.50-20050916.5-shared-qt](http://mirrors.symetrix.net/pub/ftp.opera.com/linux/850/final/en/i386/shared/opera_8.50-20050916.6-shared-qt_en_etch_i386.deb)

[QUOTE=MetalFatigue]I read in a opera forum that motif3 needs to enable multiverse repo. If someone could help a noob on how to do this, would appreciate ;)[/QUOTE]
Read the wiki entry [How-To Add Repos](http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse)

---

### Post by SadaraX on 2005-11-02
[QUOTE=Xian]Install this version of Opera: [opera_8.50-20050916.5-shared-qt](http://mirrors.symetrix.net/pub/ftp.opera.com/linux/850/final/en/i386/shared/opera_8.50-20050916.6-shared-qt_en_etch_i386.deb)
[/QUOTE]

Yes, but does that fix the plugin problem?

---

### Post by manafta on 2005-11-05
Opera requires Motif to use Netscape plugins.

sudo apt-get install libmotif3

Opera needs libXm.so.3 to be in /usr/lib. But on Breezy this file is in /usr/X11R6/lib/libXm.so.3. You will have to create a link e.g.:

sudo ln -s /usr/X11R6/lib/libXm.so.3 /usr/lib/libXm.so.3

After this, Netscape plugins should work just fine.

---

### Post by SadaraX on 2005-11-06
Thank you so much, you fixed my problem!!!!

---

### Post by Mis_Uszatek on 2006-02-17
You have fixed my problem also... almost :)

Could you tell me how to enable sound in flash in opera?

---

### Post by SadaraX on 2006-02-17
The sound problem for me arose from the fact that Opera uses OSS drivers for their audio, not ALSA. So if you have another application running that uses the sound, the OSS drivers do not function, and therefore do not put out sound. This means if you have video or music playing while browsing with Opera, you will have no audio. I solve this problem by closing my video/music programs, closing opera, restarting opera and the sound will work until I use another audio program again. I have never found a good way around this problem.

---

### Post by Mis_Uszatek on 2006-02-18
Hey

I have found an answer in different topic

[http://www.ubuntuforums.org/showthread.php?t=76743&page=2&highlight=opera+flash+sound]("http://www.ubuntuforums.org/showthread.php?t=76743&page=2&highlight=opera+flash+sound")

> I've reverted to this method since it lets me listen to flash and music from other programs simultaneously. Here is how I setup my startup scripts to create /tmp/.esd automatically on restart:

1. Goto where startup scripts are kept:
cd /etc/init.d
2. Create a "flash-sound" script...
sudo vim flash-sound (replace vim with your choice of text editor)

3. make flash-sound contents look like:

Code:

#!/bin/sh
#Create symlink under /tmp for esd to get flash player working

mkdir /tmp/.esd
ln -s /tmp/.esd-1000/socket /tmp/.esd/socket

4. make sure your new script has the correct permissions:
sudo chmod 755 flash-sound

5. finally let the system know to execute it at startup:
sudo update-rc.d flash-sound start 51 S .
(don't miss the dot "." at the end of the line above)


Now it is working great. The only problem is that sound is 0,5-1s after event.
Maybe it will be also helpful for you.

---

### Post by 4ebees on 2006-05-12
Hi manafta,

Thanks for that. I had some trouble with this and your suggestion of creating a link worked perfectly.

Many thanks.

---

