---
title: "new user has a few questions"
date: 2006-01-04
forum: Desktop Environments
---

### Post by joshua2verizon on 2006-01-04
this is my first time here at the boards, but i used Lindows once, which to be honest, just straight out sucked. Ubuntu is a great OS, but im still a little confused in a few things, so if you dont mind helping out, thanks!

first, i dont quite understand how to install an application not inlcluded in "add applications", such as Wine. I tryed the synaptic manager, but i dont understand what all the packages are. 

another issue is trying to play a media file such as an mp3 or video. I get an error dealing with the stream even though it is a saved file.

one last thing.. i would like to use this firefox extension found here: [http://quickchat.dnsalias.com:1245/](http://quickchat.dnsalias.com:1245/)  .. it is an xpi file, which i dont know how to install.

thanks a bunch!

---

### Post by darth_vector on 2006-01-04
hi, glad you like ubuntu :)

there is a great article in the wiki that explains how to get mp3's and stuff working, you can find it here: [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

when using synaptic you can enable extra repositories to increase the number of programs you can install. open the /etc/apt/sources.list file as root
```
sudo gedit /etc/apt/sources.list
```'
and uncomment all of the lines that the file tells you to.

you can then search for programs with
```
sudo apt-cache search programname
```
and install it with
```
sudo apt-get install programname
```
or with synaptic. failing this you can find deb packages or binaries on the web; these will come with instructions for installation.

hope that helps!

---

### Post by linuxted on 2006-01-04
[QUOTE=joshua2verizon]this is my first time here at the boards, but i used Lindows once, which to be honest, just straight out sucked. Ubuntu is a great OS, but im still a little confused in a few things, so if you dont mind helping out, thanks!

first, i dont quite understand how to install an application not inlcluded in "add applications", such as Wine. I tryed the synaptic manager, but i dont understand what all the packages are. 

another issue is trying to play a media file such as an mp3 or video. I get an error dealing with the stream even though it is a saved file.

one last thing.. i would like to use this firefox extension found here: [http://quickchat.dnsalias.com:1245/](http://quickchat.dnsalias.com:1245/)  .. it is an xpi file, which i dont know how to install.

thanks a bunch![/QUOTE]
Welcome aboard!  I'm sure you'll find this forum useful - I know I have.

Regarding your second question, I found a post in this forum that helped (apparently mp3 codecs get into legal mumbo gumbo)... Search for the following post "HOWTO: Breezy Sounds Nice"


Good luck

---

### Post by joshua2verizon on 2006-01-04
wow thanks alot. im now installing mplayer and codecs :)

---

### Post by az on 2006-01-04
This is an open source operating system which means that everything gets worked on using the source code.  Many people collaberate at the source code level.

This means nothing to users who only use the binary (already-compiled) packages.  Since it would be very impractical to have to gather all the sources and compile everything you run to get a system up-and-running, the linux distribution does that for you.

The catch is that you can't just click and install anything you find on the internet willy-nilly.  Something compiled for anoter distro, or another version of your distro may not work.  You would have to get that project's source code and compile it yourself.

Synaptic is just a tool to install the prebuilt packages that are available to you.  They are seperated by level of support (officially supported versus community supported) and licencing (free-libre or proprietary, but you can still distribute it)


So that is what packages are all a bout.

To use a firefox extension, you need to install it in firefox.  Firefos has an extension page to use for that.

---

### Post by joshua2verizon on 2006-01-04
actually i solved my own problem with the search! .. i noticed in an other post (the one i used), i was required to >terminal>winesetup ..

---

