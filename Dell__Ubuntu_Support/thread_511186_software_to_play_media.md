---
title: "software to play media?"
date: 2007-07-27
forum: Dell  Ubuntu Support
---

### Post by ballygowanboy on 2007-07-27
is there software for linux that can play media files.

new to linux, so far i've tried to play an .avi, and an mp3, and both won't play.

---

### Post by reckless2k2 on 2007-07-27
you need to install the restricted codecs to play them. install xine or vlc and it should get you most if not all the way there. also, query restricted formats.

---

### Post by tk03759 on 2007-07-27
Yes, there is. Ubuntu out of the box doesn't have the codecs needed to play these mp3 files. Rythmbox and Movie player will work for playing your media files just fine after you install the codecs. (Both programs come with most versions of Ubuntu).

To install the codecs, Go to Applications > Add/Remove

Make sure that "All available Applications" is selected next to the search bar. Type in "Gstreamer." Check to make sure the following are checked: "Gstreamer extra plugins", "Gstreamer ffmpeg video plugins", "Streamer plugin for aac, xvid, and mpeg2," and "Gstreamer plugins for mms, wavpack." Click apply. The installer will install the codecs.

They should work now. :)

---

### Post by jordan86 on 2007-07-28
The softwares already in Linux.
What you need to do is download the codec.
It will auto detect the codec for you.

---

### Post by ballygowanboy on 2007-07-28
> **tk03759 said:**
> Yes, there is. Ubuntu out of the box doesn't have the codecs needed to play these mp3 files. Rythmbox and Movie player will work for playing your media files just fine after you install the codecs. (Both programs come with most versions of Ubuntu).

To install the codecs, Go to Applications > Add/Remove

Make sure that "All available Applications" is selected next to the search bar. Type in "Gstreamer." Check to make sure the following are checked: "Gstreamer extra plugins", "Gstreamer ffmpeg video plugins", "Streamer plugin for aac, xvid, and mpeg2," and "Gstreamer plugins for mms, wavpack." Click apply. The installer will install the codecs.

They should work now. :)

i tried that and it didn't work :confused:

---

### Post by leftcase on 2007-07-28
Try installing VLC - see how you get on.

open a terminal, Applications > Accessories > Terminal and type sudo apt-get install vlc

Open VLC and try your media now.

---

### Post by ballygowanboy on 2007-07-28
> **leftcase said:**
> Try installing VLC - see how you get on.

open a terminal, Applications > Accessories > Terminal and type sudo apt-get install vlc

Open VLC and try your media now.

good ol vlc, that worked! just out of interest, can i download and install this kind of software the windows way? as in, an install wizzard, i'm not that technical.

that's video sorted......... i still can't play mp3, i'm using rythmbox...... looks  a bit like itunes.....

do you know how to get my ipod working on ubuntu?

---

### Post by leftcase on 2007-07-28
You know VLC can play mp3 files too? Just right click on your mp3 file and select open with vlc

Read through this help article here - it'll help you get your system set up nicely for restricted formats like mp3 - [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

As for your iPod, Ubuntu works great with iPods :guitar:

Check out this help article [https://help.ubuntu.com/community/PortableDevices/iPod?action=show&redirect=IPodHowto](https://help.ubuntu.com/community/PortableDevices/iPod?action=show&redirect=IPodHowto)

Cheers

Chris

---

### Post by leftcase on 2007-07-28
> **ballygowanboy said:**
> good ol vlc, that worked! just out of interest, can i download and install this kind of software the windows way? as in, an install wizzard, i'm not that technical.

Ooops missed that bit of your question.

One of the major differences between Ubuntu and Windows, is that the large majority of Ubuntu software is free. To help make it easier to get software, Ubuntu comes with a program which downloads and installs it for you automatically.

If you got to the menu, click on Applications and select the Add/Remove Applications option at the bottom, you can access this program.

Once it's loaded up, If you click on preferences you can select which repositories you want to be able to download software from (select 'em all!) Now, you can search for software using the search option, or navigate through it using the left hand menu - Just make sure the Show: box at the top has 'all available applications' selected.

---

### Post by ballygowanboy on 2007-07-28
i'm finding that add remove programmes wizzard doesn't work very well, but i did mannage to install amarok, using the terminal.

thanks for your help

the audio setup is a bit weird though, when i mute my laptop, the audio's still on, but sounds like someone's thrown a duvet over the laptop

---

### Post by leftcase on 2007-07-28
> **ballygowanboy said:**
> i'm finding that add remove programmes wizzard doesn't work very well, but i did mannage to install amarok, using the terminal.

thanks for your help 

No Problem :-)

Personally, I find using the terminal easier than using add/remove programs although is there a particular issue that you're having with add/remove programs?

If you decide to use the terminal instead, you can get the same kind of functionality.

To get the latest list of programs available:
sudo apt-get update

To upgrade Ubuntu and the programs installed on it:
sudo apt-get upgrade

To search for a program:
sudo apt-cache search programnamehere

To install a program:
sudo apt-get install programnamehere

To remove a program:
sudo apt-get remove programnamehere

---

