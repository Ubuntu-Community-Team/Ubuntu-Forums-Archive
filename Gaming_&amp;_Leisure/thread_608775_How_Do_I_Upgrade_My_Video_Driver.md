---
title: "How Do I Upgrade My Video Driver?"
date: 2007-11-10
forum: Gaming &amp; Leisure
---

### Post by mystik10801 on 2007-11-10
Well, someone said that the problem with SL giving an error couldn't create window had to do with the video driver... I downloaded what I am fairly sure is my video driver update, but when I try to install it, it says I have to exit X server, which I was told means log in as root, so I did init 1 and got on as a root, but then I couldn't install the driver because the root directory is missing a graphics kernel or something... someone said run apt-get, which doesn't seem to be getting ANYTHING, because I whether I search for mplayer or nvidea, it says file not found or archive not found, one or the other... and WHAT'S THE FREAKIN' DEAL WITH NOT BEING ABLE TO PLAY AN MP3 OR MPEG FILE?

---

### Post by cogadh on 2007-11-10
Its not the video driver that prevents you from running those files, its the codecs. Go to "Add/Remove Programs", search for and install the following:
GStreamer ffmpeg video plugin
GStreamer extra plugins
GStreamer plugins for aac, xvid, mpeg2, faad
GStreamer plugins for mms, wavpack, quicktime, musepack

Then go [here](https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f) and follow the instructions for adding the MediBuntu repositories, then install the Win32 codecs package:
```
sudo apt-get install w32codecs
```
If you want to watch DVDs, you'll also need to install the css package:
```
sudo apt-get install libdvdcss2
```

As for installing your video driver, all you usually have to do is go to the Restricted Drivers Manager application and enable the Nvidia driver.

---

### Post by mystik10801 on 2007-11-10
apt-get has gotten me nothing any time I've tried to run it... always says it can't find the file... got all that other stuff done though...

---

### Post by cogadh on 2007-11-10
Try running this first:
```
sudo apt-get update
```
That refreshes the package list with the info from all the repositories, inlcuding the MediBuntu ones you just added. I thought that step was part of the MediBuntu instructions, but I guess not.

---

### Post by mystik10801 on 2007-11-10
yeah, "update" worked... but when I tried to get the w32codecs it said it was dependent on libstdc++5, but that it was not installable and that a bug report on this command should be filed :/
SL still gives a window creation error also

---

### Post by mystik10801 on 2007-11-10
I might still need to do these other things you mentioned, but 100% an issue is the fact that Linux isn't using the proper video driver, and it won't let me install it from the shell, or from root

---

### Post by cogadh on 2007-11-10
What is SL? What version of Ubuntu are you using? Have you tried enabling the restricted driver as I mentioned in the initial response?

---

### Post by mystik10801 on 2007-11-10
SL is SecondLife... a lot of ubuntu users are running it, or a lot of SL linux users are running ubuntu, either way... I think I've got the "whatever-faun" version... idk... I can't even seem to get this IM program to load so I can do live chat with anyone who can help that way.

---

### Post by cogadh on 2007-11-10
Ah, Second Life, that makes sense now. Random acronyms always confuse me.

You really need to be sure which version of Ubuntu you have, it would help with pointing you to the correct solutions. 

You didn't answer the question about the restricted driver. Just an FYI, the restricted driver is the current stable driver from Nvidia that is available for install in Ubuntu through the package manager. It is generally the best way to get a functional accelerated driver on Ubuntu. Using the one that you download from Nvidia could lead to problems later down the line and is much more difficult to do anyway.

---

### Post by mystik10801 on 2007-11-10
OK then, I'll just delete this driver I got off their site and try to get one specifically for ubuntu... I have a geforce 5500 agp 4X with 256mb of ram... how do I get the right driver for that? right now it's using a generic geforce4 driver

---

### Post by mystik10801 on 2007-11-10
I just found the driver manager window, as well as the video driver display selector window (eh, whatever you want to call it), and it reads that the video driver is 1. not the right driver; and 2. not enabled... it gave me an error when I clicked to enable it that said glx-nvidea-new not enabled

---

### Post by mystik10801 on 2007-11-10
"the software source for the package nvidea-glx-new is not enabled" was the verbatim message gotten when trying to enable the driver

---

### Post by JBAlaska on 2007-11-10
You need to enable all the repositories in system>>administration "software sources".

Since I use ATI I can't tell you which one,the restricted driver manager should tell you which. **edit: proprietary drivers for devices (Restricted) **

After you get the video driver installed you can go to the third party software tab and add the medibuntu repo's for your dvd and mp3 stuff;
```
http://www.medibuntu.org/
```

---

### Post by mystik10801 on 2007-11-10
Yeah, you were right... I had to go into add/remove programs and click the preferences button... then I had to check every box under the first tab (all were unchecked), unselect the unfree sources and select the partner sources in the updates tab (that's why apt-get wasn't getting anything) and at that point I was able to enable my video card under system>administration>restricted drivers manager... things are running and working a lot smoother now, but all of a sudden I'm getting an error within my file retrieve browsers in any media program I try to import my media files from that says "The Folder Contents Could Not Be Displayed"

---

### Post by mystik10801 on 2007-11-10
I also just did a sudo apt-get install ubuntu-restricted-extras and I got cool stuff like Java and Flash and some other essential "extras"... hehehe... I'm gonna have to start a Linux Noob page when I get this stuff figured out... "crash course to get you goin' in a day" *shrugs*

---

### Post by Sockerdrickan on 2007-11-10
It's not very hard at all. Think before you act, that's all I can say.

---

