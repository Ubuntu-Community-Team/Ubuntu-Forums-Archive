---
title: "mplayer requirements?!"
date: 2005-02-26
forum: Desktop Environments
---

### Post by RastaMahata on 2005-02-26
This is weird... I followed the instructions from [http://www.ubuntulinux.org/wiki/RestrictedFormats](http://www.ubuntulinux.org/wiki/RestrictedFormats) to install mplayer-k7

mplayer-k7 didnt work. so i tried mplayer-k6

and the requirements are dumb:
libdirectfb-0.9-20
libfaad2-0
libggi2
liblame0
libpostproc0
libsvga1
libxvidcore4
xmms

I can understand the requirements of those libraries, but xmms? WHY?! I dont use xmms.

I tried to remove xmms, but then apt-get told me it would remove mplayer. What the hell is wrong?! (I'm using warty)

---

### Post by RastaMahata on 2005-02-26
bump

---

### Post by RastaMahata on 2005-02-27
[QUOTE=RastaMahata]bump[/QUOTE]
 double bump?

---

### Post by kahping on 2005-03-05
i find this strange too; i tried installing mplayer after upgrading to hoary and i have to same thing here. 

why would xmms be a dependency for mplayer? doesn't look like mplayer uses xmms for anything. i've compiled mplayer before and it worked perfectly fine without xmms. i hope this is just a simple oversight and gets fixed by hoary release

kahping

---

### Post by bored2k on 2005-03-05
Also i installed mozilla-mplayer becuz of the streaming video thing , and it installed mplayer-custom, wich WONT open , it will just freeze if i try to open it [only works thru firefox]..

a  fix to these? will the other 686 or 386 work with streaming [i really n33d streaming - vlc-mozilla-plugin is not good here] ??

---

### Post by brk3 on 2005-03-05
How about trying compiling from source? Or use xine, I find it much better than mplayer :)

---

### Post by luvdemheels on 2005-03-05
I am trying to figure out where to put the codecs (dll files) after installation of mplayer. I installed using sudo apt-get install mozilla-mplayer.

Does anybody know??? I did a find for codecs buut cam up with nothing associated with mplayer.

---

### Post by RastaMahata on 2005-03-05
mplayer-custom was compiled for pentium4 only. Maybe that's why it doesnt work.

Here's a little and easy howto for warty. I got a lot of help from this post: [http://www.ubuntuforums.org/showthread.php?t=94](http://www.ubuntuforums.org/showthread.php?t=94) and from [http://www.ubuntulinux.org/wiki/RestrictedFormats](http://www.ubuntulinux.org/wiki/RestrictedFormats) ;)

I think this is the best way to get mplayer running easily and fast. The only downside: xmms. I dont know why the hell you must have it, and I hope this gets fixed for hoary. Well, here we go.

> 
First of all, we're gonna update our whole ubuntu system. We should follow the following steps (Taken from [www.ubuntuguide.org](www.ubuntuguide.org)):

First, update your /etc/apt/sources.list:```
$ sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
$ sudo gedit /etc/apt/sources.list
```Delete the whole thing, and copy-paste this:```
deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted 


## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu/ warty main restricted
deb-src http://archive.ubuntu.com/ubuntu/ warty main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ warty universe
deb-src http://archive.ubuntu.com/ubuntu/ warty universe

deb http://security.ubuntu.com/ubuntu/ warty-security main restricted
deb-src http://security.ubuntu.com/ubuntu/ warty-security main restricted

deb http://archive.ubuntu.com/ubuntu/ warty multiverse
deb-src http://archive.ubuntu.com/ubuntu/ warty multiverse

deb ftp://ftp.nerim.net/debian-marillat/ stable main
deb ftp://ftp.nerim.net/debian-marillat/ unstable main
deb ftp://ftp.nerim.net/debian-marillat/ testing main

deb http://ubuntu-bp.sourceforge.net/ubuntu/ warty-backports main universe
```Now, we follow these steps:```
$sudo apt-get update
$sudo apt-get upgrade
```Now we are able to install the codecs, mplayer and the plugins. ;)

Open up a console and do this:```
sudo apt-get install manpages-dev autoconf automake libtool flex bison gcc-doc g++ x-window-system-dev libgtk1.2-dev libpng12-dev libgtk2.0-dev libdirectfb-0.9-20 libfaad2-0 libggi2 liblame0 libpostproc0 libsvga1 libxvidcore4 xmms gstreamer0.8-plugins w32codecs
```Then we get our hands dirty  :) .

Let's create a "work" folder in our home folder so we dont get our folders all messy:```
mkdir ~/work
```Now we change into that folder and download the corresponding version of mplayer for our CPU.

If you use warty, get mplayer from here:```
http://sh.nu/~crimsun/mplayer/
```For example, if you have a pentium 4, get the 686 version. For Athlon (XP), get k6 (as k7 is just a dummy package).

Download it to the recently created "work" folder.

Next, we will install it:```
cd ~/work
sudo dpkg -i mplayer-*
```Now we have mplayer. You can run the following command to run it:```
gmplayer
```Dont worry if it doesnt appear in your Multimedia menu, it will when you reboot your x server (by pressing ctrl+alt+backspace if you dont want to reboot your pc).

Now that we have mplayer running, close it :P, we will have to get the plugins. Unfortunately, the mplayer plugins for mozilla that ubuntu has just suck. So we will make our own (dont worry, it too easy).

First, get these files, and download them to your work directory!:```
http://ftp.mozilla.org/pub/mozilla.org/mozilla/releases/mozilla1.6/gecko-sdk-i686-pc-linux-gnu-1.6.tar.gz
http://prdownloads.sourceforge.net/mplayerplug-in/mplayerplug-in-2.70.tar.gz?download
```Now open a console and do this:```
cd ~/work
tar -xzvf gecko-sdk-i686-pc-linux-gnu-1.6.tar.gz
tar -xzvf mplayerplug-in-2.70.tar.gz
cd mplayerplug-in
./configure --with-gecko-sdk=~/work/gecko-sdk
make
```Now, if you have firefox, do this:```
sudo cp ~/work/mplayerplug-in/mplayerplug-in.so /usr/lib/mozilla-firefox/plugins
sudo cp ~/work/mplayerplug-in/mplayerplug-in.xpt /usr/lib/mozilla-firefox/components
```And for the mozilla suite, do this:```
sudo cp ~/work/mplayerplug-in/mplayerplug-in.so /usr/lib/mozilla/plugins
sudo cp ~/work/mplayerplug-in/mplayerplug-in.xpt /usr/lib/mozilla/components
```Now close all your firefox/mozilla windows and open a new one. To test the plugin, go here:```
http://www.apple.com/trailers/
```And watch a trailer. Have fun! ;)

---

