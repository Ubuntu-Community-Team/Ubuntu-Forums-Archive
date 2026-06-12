---
title: "Newbie Help Duke Nukem 3D"
date: 2011-04-24
forum: Gaming &amp; Leisure
---

### Post by boldhoof on 2011-04-24
Hi

I would love to play my old Duke Nukem 3D and all the add -ons on Xubuntu. The problem is I only know very basic stuff, and it seems you need to compile eduke32 which has me lost. Looked at dosbox but got no idea how to install the game. Anyone able to give me an idiots step by step guide please.

Many thanks
Gerry

---

### Post by HoKaze on 2011-04-24
You don't have to compile anything, there's a repository on the eduke32 website with instructions: [http://wiki.eduke32.com/wiki/APT_repository](http://wiki.eduke32.com/wiki/APT_repository)
I'll sum it up in brief: 

1. Edit */etc/apt/sources.list* as root with your preferred text editor or open synaptic package manager -> settings -> repositories -> other software ->

2. Add ```
deb http://apt.duke4.net YOUR_UBUNTU_VERSION_HERE main 
deb-src http://apt.duke4.net YOUR_UBUNTU_VERSION_HERE  main
``` to the file (or apt line box if you're using synaptic)

3.  Close synaptic if it's open and copy-paste this into the terminal: ```
wget -q http://apt.duke4.net/key/eduke32.gpg -O- | sudo apt-key add -
```4. Synaptic method: Open synaptic package manager, hit reload and search for the eduke32 package, then install it.
Command line method: sudo apt-get update; sudo apt-get install eduke32

---

### Post by boldhoof on 2011-04-24
Many thanks I have that installed now. Now just to work out how to get the add-on discs to work, thanks for the help. If you know how to do the add on discs like nuke winter etc would be excellent.

---

### Post by HoKaze on 2011-04-24
I'm not 100% sure when it comes to the add-on disks and various mods but I think if you search the disk you should find a file called "nwinter.grp" or something along those lines. If you place this in your eduke directory (/home/username/.eduke32/) with all your other duke3d files, then launch eduke32, you should get a startup window. Click the "game" tab and you should have duke3d, possibly the shareware version and nuclear winter listed. Select the appropiate game and click start.

For extras like any music packs, 3d models or the high resolution pack your best bet is to search the wiki and forums.

---

### Post by HolgerB on 2011-04-26
I am running Duke3D inside DOSBox. So I can not comment on Eduke32 too much.

All Build games though rely on GRP files which are pretty similar to WAD files (for DOOM games). So unless the grp-files of each add-on are not packaged inside any installation files I would simply copy them over to the eduke32 directory.

As for DOSBox the complete installation process is pretty straightforward. There is also a wiki entry:
[https://help.ubuntu.com/community/DOSBox](https://help.ubuntu.com/community/DOSBox)

---

