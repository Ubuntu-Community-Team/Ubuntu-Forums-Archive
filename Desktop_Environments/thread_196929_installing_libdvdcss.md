---
title: "installing libdvdcss"
date: 2006-06-15
forum: Desktop Environments
---

### Post by arthurbarnhouse on 2006-06-15
I did a search, but I couldn't find anything for this specific situation.  The only thread I found was for installing libdvdcss2, which dosn't seem to have solved the problem.  So, how do you install libdvdcss?  it doesn't appear on the Synaptic Package Manager, and manual downloads have been failures.

Also, please bear in mind this is my first time trying Linux, so I don't know anything about terminal.  My last OS was  OS X.

---

### Post by mattkenn4545 on 2006-06-15
The Wiki has a command that will install libdvdcss2 that should work for decoding dvds 

sudo /usr/share/doc/libdvdread3/examples/install-css.sh

What are you using to play DVD'd if trying to use totem it isn't working (at least the gstreamer backend) 

I Use gxine for all my DVD Needs

here are the packages that I install to get media to work correctly

Also could put this into a text document and make it executable with chmod +x <name-of-file>

## Commands to get Ubuntu 6.06 up-and-running

#/bin/bash
# Multimedia
wget -c [ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.4_i386.deb](ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.4_i386.deb) 
sudo dpkg -i w32codecs_20050412-0.4_i386.deb

sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-pitfdll gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse totem-gstreamer-firefox-plugin gxine sun-java5-bin sun-java5-plugin sun-java5-fonts acroread acroread-plugins mozilla-acroread flashplugin-nonfree msttcorefonts xmms xmms-status-plugin xmms-skins debfoster easytag audacity mplayer

rm -f ~/.gstreamer-0.10/registry.i486.xml

# update flashplugin
sudo update-flashplugin

# Lets to decrypt DVDs
sudo /usr/share/doc/libdvdread3/examples/install-css.sh

# Set the java provider
sudo update-alternatives --set java /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

---

### Post by not_yet on 2006-06-15
first update your sources list, add the following

deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free

then

sudo apt-get update

then

sudo apt-get install libvdcss2

your sources list is at /etc/apt/sources.list

open gedit from a terminal like so

sudo gedit

then navigate to the file you are going to edit

cheers

---

### Post by Phlosten on 2006-06-15
You should be able to use this package:

[http://mdk.linux.org.tw/ftp/pub/plf/ubuntu/plf/pool/dapper/i386/free/libdvdcss2/libdvdcss2_1.2.9-1plf3_i386.deb](http://mdk.linux.org.tw/ftp/pub/plf/ubuntu/plf/pool/dapper/i386/free/libdvdcss2/libdvdcss2_1.2.9-1plf3_i386.deb)

Download it and open and install it with the Gdebi package installer. It is not seen by default in the menu but if you go into the Alacarte Menu Editor you will see it in System Tools. Tick the box and it will be available in the menu.

---

