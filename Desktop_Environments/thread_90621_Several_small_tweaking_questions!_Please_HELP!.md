---
title: "Several small tweaking questions! Please HELP!"
date: 2005-11-15
forum: Desktop Environments
---

### Post by linkunderscore on 2005-11-15
I am running Breezy now, but I noticed a couple things after the upgrade that have change that I would like to change back. 

**Question #1:**

What do I have to edit/change so that Nautilus opens with the location bar instead of the tabs? (Pressing Crtl+L will do this but I would not like to have to do that everytime I open it)  *Also: If its a Gconf setting change--whats the command line command to start gconf?*

[B][I][COLOR="DarkOrange"]SOLVED: 
Open the Gconf editor and go to /apps/nautilus/preferences/ and you have the option always_use_location_entry to modify that.
Thanks to Frodon! 

sudo gconf-editor opens Gconf btw[/COLOR][/I][/B]

[B]
Question #2:[/B]

I run Ubuntu with FVWM. I use gnome-settings-daemon to make my windows look like the pretty gnome theme i have installed at the time. Open Office programs however do not apply the gnome theme (gtk).  I remember fixing this in Hoary by uncommenting a config file for OOo. It was something like FORCE OOo "FORCE=DESKTOP" "gtk" or something rather. :confused: 

I have looked everywhere online, but -for the life of me- can not find out how I did it before. 
[B][I][COLOR="DarkOrange"]
SOLVED: 

Edit the /etc/openoffice/openoffice.conf file to say:

```
export OOO_FORCE_DESKTOP=gnome
```
If this fails to work, like it did for me the second time I attempted it(worked the first time :shrug:), use synaptice to remove all Open Office 2 files (COMPLETE REMOVAL). Then reinstall everything including the openoffice.org2-gnome package which uses gnome support. Then start it up: :)[/COLOR][/I][/B]

[B]
Question #3[/B]

I have installed the latest Firefox RC and I prefer to use this over the firefox that comes with breezy. ATM I have to /usr/lib/firefox/firefox./firefox  to run it. After its already running--typing 'firefox' in console will open another window of 1.5. If I type firefox in console without having 1.5 running (the /usr/~ way) It starts 1.0.7. 

I am pretty sure its because i need to ln -s (make a symbolic link) from /usr/lib/firefox/firefox./firefox to /usr/bin/ . I am a novice with linux so I was just wondering if thats what I have to do and if i have to delete the symlink that is already there (the one that points to 1.0.7)--i figure that might cause a problem.

Should I just apt-get remove mozilla-firefox(1.0.7) completely? 
[B][I][COLOR="DarkOrange"]
SOLVED:
check out the Wiki installation instructions for Firefox 1.5 at:

[https://wiki.ubuntu.com/FirefoxNewVe...=%28firefox%29](https://wiki.ubuntu.com/FirefoxNewVe...=%28firefox%29)
Thanks for writerman for pointing this out.[/COLOR][/I][/B]

[B]
Question #4[/B]

When I right click on a .wma file to Open With MPlayer --there are 2 MPlayer options in the menu (both work). How do I remove one of those options? I don't need 2. 
[B][I][COLOR="DarkOrange"]SOLVED:

Right-click on the file you want, click Properties and find the tab called "Open With". In there it should be a lot of options to choose. You can now select one of the two, and click on the delete button in the same window. It is also possible to add new ones. 
Thanks to magnusbb[/COLOR][/I] [/B]

**Question #5 **

Related to Question #4. It opens all media by default with Totem. Now that wouldn't be so bad IFF totem could play anything :|  Totem can't play anything I have tried to play. So my question is: How can I install codecs for quicktime movies, wma's, mpegs, realmediafiles etc???  Right now I am always forced to right click and use mplayer to play most of my files. 

I heard Totem is suppose to be ALOT better and nicer in Breezy, but im not seeing it.
[B][I][COLOR="DarkOrange"]SOLVED:
install xine, and all the codecs, plus win32codecs. Then install the totem-xine exstension.[/COLOR][/I][/B]

Thanks for your help :) !

---

### Post by frodon on 2005-11-15
Question #1 :
Open the Gconf editor and go to /apps/nautilus/preferences/ and you have the option always_use_location_entry to modify that.

---

### Post by linkunderscore on 2005-11-15
Thanks Frodon :)

---

### Post by magnusbb on 2005-11-15
Question 4:

Right-click on the file you want, click Properties and find the tab called "Open With". In there it should be a lot of options to choose. You can now select one of the two, and click on the delete button in the same window. It is also possible to add new ones. I really like GNOME's way of doing this. Used to be very complex.

Question 5:
My solution would be to install xine, and all the codecs, plus win32codecs. Then install the totem-xine exstension. Now Totem should rely on Xine, and play whatever you want. And, yes, Totem has become a good application. (Finally).

---

### Post by frodon on 2005-11-15
By the way, try the totem-xine package, it will sove a lot of problems using totem.
For wma files, you need w32codecs and also libdvdcss2 for dvd's : [http://www.ubuntuforums.org/showthread.php?t=81577&highlight=w32codecs](http://www.ubuntuforums.org/showthread.php?t=81577&highlight=w32codecs)
[http://www.ubuntuforums.org/showthread.php?t=75278&highlight=w32codecs](http://www.ubuntuforums.org/showthread.php?t=75278&highlight=w32codecs)
[http://www.ubuntuforums.org/showthread.php?t=79449&highlight=w32codecs](http://www.ubuntuforums.org/showthread.php?t=79449&highlight=w32codecs)

If i remember well there's a package called quicktime in synaptic which install quicktime codecs.

If you really dislike totem you can replace the default application to be mplayer : [http://www.ubuntuforums.org/showthread.php?t=76946&highlight=mplayer](http://www.ubuntuforums.org/showthread.php?t=76946&highlight=mplayer)

---

### Post by linkunderscore on 2005-11-15
[QUOTE=magnusbb]Question 4:

Right-click on the file you want, click Properties and find the tab called "Open With". In there it should be a lot of options to choose. You can now select one of the two, and click on the delete button in the same window. It is also possible to add new ones. I really like GNOME's way of doing this. Used to be very complex.

Question 5:
My solution would be to install xine, and all the codecs, plus win32codecs. Then install the totem-xine exstension. Now Totem should rely on Xine, and play whatever you want. And, yes, Totem has become a good application. (Finally).[/QUOTE]

Gracias

---

### Post by canadianwriterman on 2005-11-15
For question #2, check out the Wiki installation instructions for Firefox 1.5 at:

[https://wiki.ubuntu.com/FirefoxNewVersion?highlight=%28firefox%29](https://wiki.ubuntu.com/FirefoxNewVersion?highlight=%28firefox%29)


Hope that helps!

---

### Post by linkunderscore on 2005-11-15
link@link:~$ sudo apt-get install xine-ui ; totem-xine
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libmodplug0c2 libslang2-dev libxine-dev libxine1c2
The following packages will be REMOVED:
  libmodplug0 libxine1 slang1-dev
The following NEW packages will be installed:
  libmodplug0c2 libslang2-dev libxine1c2 xine-ui
The following packages will be upgraded:
  libxine-dev
1 upgraded, 4 newly installed, 3 to remove and 0 not upgraded.
Need to get 0B/6547kB of archives.
After unpacking 4977kB of additional disk space will be used.
Do you want to continue [Y/n]? y
E: Internal Error, Could not perform immediate configuration (2) on libxine-dev
bash: totem-xine: command not found


any suggestions?

---

### Post by frodon on 2005-11-15
Maybe, you haven't all the repositories enabled, post here your source.list file (sudo gedit /etc/apt/source.list) to be sure.

---

### Post by linkunderscore on 2005-11-15
```

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu breezy main universe multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main universe multiverse restricted

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe
```

Just the basic breezy repos.

---

### Post by linkunderscore on 2005-11-15
BUMP for the night crew ;)

---

### Post by linkunderscore on 2005-11-15
Helpp Meeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeee:ks

---

### Post by linkunderscore on 2005-11-16
I got 3.5 of my 5 questions answered in an hour of the original post but nothing since. :(

Does anyone know the answer to Question #2??

---

### Post by linkunderscore on 2005-11-16
It wouldn't install because E17 and its programs were relying on libxine-dev the way it was. I just removed all e17 stuff and libxine and reinstalled it. (i dont use e17 anyway). 

Should work now :)

---

### Post by linkunderscore on 2005-11-17
only one question that hasn't been answered. The one thats been bugging me for the longest.

#2! ahhhhh

---

### Post by linkunderscore on 2005-11-20
....#2 :(

I found the file I am suppose to edit. /etc/openoffice/openoffice.conf

```
#
# STAR_PROFILE_LOCKING_DISABLED=1
# export STAR_PROFILE_LOCKING_DISABLED
#

#
# SAL_ENABLE_FILE_LOCKING=1
# export SAL_ENABLE_FILE_LOCKING
#

# uncomment this to remote start soffice on hostname  
# SO_REMOTE_START=rsh
# SO_REMOTE_APPLICATION=hostname:/fully_quallified_path/soffice

# write to M$ Office formats per default?
#export OOO_MS_DEFAULTS=1

# force OOo to use theme settings from gnome or KDE or disable?
# set to 'gnome', 'kde' or 'none' to override the autodetection
export OOO_FORCE_DESKTOP=gnome

```

That bit of code should do it. BUT ITS NOT!!! GRRRRrrrrrr

---

### Post by linkunderscore on 2005-12-03
Fixed it.

Used synaptice to COMPLETELY REMOVE anything related to open office org. Reinstalled everything making sure to include the "gnome support". 

Started it right up.

---

