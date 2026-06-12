---
title: "Major Newbie on Ubuntu...HELP!!"
date: 2005-10-15
forum: Desktop Environments
---

### Post by Gere2255 on 2005-10-15
Well today i decided to install Ubuntu because i've requested the CD and i got it a while back and my windows was acting extremely horrible.  Ubuntu is great by the way!! Well here are a few things... i need help basically installing new music players so i can play MP3 Files, if you guys can help i would greatly appreciate it.  Also I would like to know if i could bump my resolution up a bit because now its at 1024x768 and i want it higher.  Also i would like to know how i would be able to stream videos on the web, like on gamespot.com or things like that.  Also i had another partition of 100gb on this computer before i reformatted another partition with windows on it to install Ubuntu... how would i be able to get the partition and view it??  There are many more questions but if you guys can help me on this i would greatly appreciate it..thanks a lot :smile:

---

### Post by brentoboy on 2005-10-15
I can help with some of this...

Open synaptic (system menu > administration > synaptic package manager)

get xmms if you dont have it.
xmms is an audio player - sort of like winamp.  it has plugins - like mp3 support.

Search for "xmms mp3" - make sure you search package names and descriptions.

look through the items in the result list and see if any of them look like a plugin to play mp3s.

maybe gnomp3 will do what you want.  Look around.  there's so much stuff in there, something will do what you need.

---

### Post by brentoboy on 2005-10-15
to help with your resolution, I need more info, open this file:

/etc/X11/xorg.conf

its just a text file.
look for the section that looks like this:
Section "Device"
	Identifier	"NVIDIA Corporation NV43 [GeForce 6200]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection

it will tell you what graphics card was detected, and what driver it is using.  Post it, lets see what you've got.

Also, look for the section like this
Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV43 [GeForce 6200]"
	Monitor		"Samsung SyncMaster 213T"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200"
	EndSubSection
EndSection

it lists the display modes you would like to be available.  X-server will grab what is listed here, and try to use the best one listed in the section. it will work its way down from best to worst, and go with the first one that works properly (if all goes well).

Dont change anything yet (you would have to be root to change it anyway) just look and see if it looks like it is right to you.  Is your desired resolution even listed there?

---

### Post by stoffe on 2005-10-15
First of all, enable universe and multiverse repositores: [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

Then, for mp3 support in apps you already have, add gstreamer0.8-mad - probably easier to simply add gstreamer0.8-plugins, which adds this and support for other formats as well. They aren't included by default due to legal reasons.

If you still want other players, there are lots to choose from, like xmms, muine, bmp and so on. You'll have to find which ones you like yourself. :)

The resolution can probably be bumped up by installing proper drivers for your graphics card, with some more info about which one, you can get help with this too. That is, if you can't go higher under System->Preferences->Screen resolution.

Streaming media might be a bit more tricky, I'm not sure which plugins currectly work... although many standalone players can handle streams if provided the url - that's an extra step though.

---

### Post by 11hjpphty76lkjj on 2005-10-15
For mp3s I use amarok with the gstreamer0.8 plugins.  As for your other questions:

[http://ubuntuguide.org/](http://ubuntuguide.org/)

For your resolution you can try (in a terminal) sudo dpkg-reconfigure xserver-xorg.  Although you may want to back up your current xorg.conf; cp /etc/X11/xorg.conf /etc/X11/xorg.conf_bak
then if it doesn't work type; cp /etc/X11/xorg.conf_bak /etc/X11/xorg.conf

Although the ubuntuguide is a tad dated with Breezy, but it might help some.

Aaron

---

### Post by Gere2255 on 2005-10-15
Thanks a lot guys, i will try my best, im really excited about this OS... hopefully i can get all of my games to run!!!

---

### Post by 11hjpphty76lkjj on 2005-10-15
For games try wine or Cedega.  Wine works, I got Empire Earth to run with it.  As does Cedega, but you have to buy Cedega.  Don't go back to windows cause of the games, they (well should anyway) work, but it takes some time working it out.  There is some good wine how tos.  I haven't used Cedega but I'm sure someone has some good tips for it.

Aaron

---

### Post by Gere2255 on 2005-10-15
I also need help in installing files... i just dont understand how all of this works....

---

### Post by brentoboy on 2005-10-15
Applications Menu > Add Applications

that will give you the basic stuff.

That screen has an advanced area - that brings you to synaptic (which you can launch independantly from the system menu > administration > synaptic)

this is a big list of every package available to you from the huge ubuntu repositories of avaialbe stuff.  you can search and sort it to find what you want.

rather than looking for programs you know (from windows) search for the same type of subject matter and see what is avaialble here.

do a quick search of the forums and the wiki for how to add the universe and multiverse repositories - they arent technically supported, but their is even more stuff when you add them.

after playing with it just a little bit, you will start to feel like the world is at your fingertips.

---

