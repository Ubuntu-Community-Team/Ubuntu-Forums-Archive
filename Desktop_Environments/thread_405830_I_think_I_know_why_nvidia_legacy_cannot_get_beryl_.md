---
title: "I think I know why nvidia legacy cannot get beryl to work!"
date: 2007-04-10
forum: Desktop Environments
---

### Post by Masterj15 on 2007-04-10
I think I know why beryl cannot run on nvidia legacy cards. I did some looking up on why I needed and turns out that their is an extention called the GLX_Pix_Extension (or something like that. I am not sure beacuse I am not at my computer right now,but people know what I'm saying beacuse when the run beryl in the terminal they see this come up and mess up their computer srceen.) 

The mesa 6.5 does have this extension but your legacy kernel does not support this. I could be wrong but I did some infomation and searching on it. I did hear that it was supported some time ago but then a nvidia forums moderater said that they do not anymore. 

If anyone knows of legacy supporting this extion or anything like it please report it hear. Do not feal bad for your selves who have a old nvidia card. 

In the mean time you can download 3ddesk and 3ddeskfx if you want awsome flipping screen and a 3d box. This program can even do some things that the beryl cannot. It can flip over like a double side. Try this until you get a better graphics card.


Please tell if you know a person or anyone who has this extion or anything like it running please.

Thanks in advance:)

---

### Post by FuturePilot on 2007-04-10
I need the Legacy driver but I can get Beryl to work, although I get that error about the GLX_EXT thing, but it works:-| I too would like to know about this extension, if it even exists.

---

### Post by Masterj15 on 2007-04-10
Are you saying you need the legacy driver so you can make it work beacuse in that case that means that you would have to go to pacakges.ubuntu.com to get that legacy. If you get this to work or you already have please tell me beacuse I have been working on that thing for about 5 months with a whole bunch of probablems.:)

---

### Post by FuturePilot on 2007-04-10
You could just ```
apt-get install nvidia-glx-legacy
```
or you could use Envy and it will get you the correct latest driver. What version of Ubuntu are you using?

---

### Post by Masterj15 on 2007-04-11
I have all that already. Sorry I should say what I mean better. If you got the nvidia legacy diver and the kernel to work with beryl at all can you tell me beacuse I do not think it is possible. I tried to make an xgl session but it did not work. I don't know why and I ave looked at alot of things. What makes it worse is that I had it working before my computer crashed and I had to install ubuntu again. 


Ubuntu egdy eft 
Nvidia tnt2/tnt2 pro
381mb of ram (I know I need moreLOL):)

---

### Post by kikdadog on 2007-04-11
OK, Im a complete noob, but this is what I did to get it working. Installed envy and automatix2, used envy to uninstall all the previous drivers, then automatix to install the nvidia driver, 8776 is what I use. Then install beryl. Just saying it worked for me.

---

### Post by compiledkernel on 2007-04-11
For diagnosis of nvidia issues try here - [https://help.ubuntu.com/community/NvidiaTroubleshooting](https://help.ubuntu.com/community/NvidiaTroubleshooting)

For future reference to Automatix please refer here - [http://ubuntuforums.org/announcement.php?f=13](http://ubuntuforums.org/announcement.php?f=13)

---

### Post by Masterj15 on 2007-04-11
I can't use any one those things beacuse I don't have internet on that computer. I have to download the deb packages or the source.:(  Also you still have a higher kernel then me. I have the7117 or something like that.:confused:

---

### Post by Masterj15 on 2007-04-11
This is what I'm going to do. I am going to show you links of sites that tell me that i could get the nvidia kernel 7148 or something like that to work with beryl. It is not like I have any money to buy anything. I just a kid trying to get beryl to work. 

[http://gentoo-wiki.com/HARDWARE_Video_Card_Support_Under_XGL#nVidia_Cards](http://gentoo-wiki.com/HARDWARE_Video_Card_Support_Under_XGL#nVidia_Cards)

[http://gentoo-wiki.com/HOWTO_XGL](http://gentoo-wiki.com/HOWTO_XGL)

scroll down and see how it has the  GLX thing I was talking about before.


[http://www.nvnews.net/vbulletin/showthread.php?t=89350](http://www.nvnews.net/vbulletin/showthread.php?t=89350)

[http://lists.freedesktop.org/archives/xorg/2006-February/012760.html](http://lists.freedesktop.org/archives/xorg/2006-February/012760.html)

more links will be added
:D

---

