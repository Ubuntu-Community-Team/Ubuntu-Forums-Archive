---
title: "Playing embedded video in Epiphany or Firefox"
date: 2006-02-21
forum: Desktop Environments
---

### Post by Morbett on 2006-02-21
I've tried installing different packages... mplayer, xine...  I'm still unable to play embedded videos in Epiphany.  The mplayer window will show a progress bar but it will never completely load and the video never plays.  

Does anyone know a sure-fire way to get videos to play?

Thanks.

---

### Post by nanotube on 2006-02-21
maybe its something wrong with that particular site. try going to another site with embedded video and see if that works?

also, might want to install newest version of firefox ([http://wiki.ubuntu.com/FirefoxNewVersion)](http://wiki.ubuntu.com/FirefoxNewVersion)), and newest version of mplayer from the backports repository, and see if that helps any.

---

### Post by akiro.yamamoto on 2006-02-21
You need the mplayer plugin. I had the same problem.
Google is your friend

---

### Post by akiro.yamamoto on 2006-02-21
Try this link:
[http://mplayerplug-in.sourceforge.net/](http://mplayerplug-in.sourceforge.net/)
Akiro

---

### Post by jslmg on 2008-01-09
I'm also trying to get video and audio to play reliably in Epiphany. I can play youtube videos with sound, so that's OK. I can play BBC videos, but no sound (BBC videos and audio are .asx files). I can't get any video or sound from CNN--tells me to make sure I don't have any "Flash blocking plugins." This is also true in Firefox.

Can anyone offer further help with this?

I tried to install That mplayerplug-in. It  is tricky, tricky, tricky.

Here's the output when I ran ./configure:

```
macubuntu@Ubuntu:~/Desktop/mplayerplug-in$ ./configure
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for a BSD-compatible install... /usr/bin/install -c
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
configure: Determining mozilla/firefox packages to build against
checking for pkg-config... /usr/bin/pkg-config
checking for mozilla-plugin... configure: WARNING: mozilla-plugin not found
checking for firefox-plugin firefox-xpcom... configure: WARNING: firefox-plugin not found
checking for seamonkey-plugin... configure: WARNING: seamonkey-plugin not found
checking for xulrunner-plugin... configure: WARNING: xulrunner-plugin not found
checking for iceape-plugin... configure: WARNING: iceape-plugin not found
configure: error: Unable to find mozilla or firefox development files
macubuntu@Ubuntu:~/Desktop/mplayerplug-in$ ./whatoptions.sh
sh: gtk-config: not found
sh: gtk-config: not found
sh: gtk-config: not found
Run configure with the following options

./configure --enable-gtk1 --with-mozilla-home=/usr/lib/iceweasel --with-gecko-sdk={path to gecko sdk}

You need to install the gecko-sdk

macubuntu@Ubuntu:~/Desktop/mplayerplug-in$
``` 

Notice that I ran ./whatoptions.sh. Where do I get the gecko-sdk? It's not in synaptic. Notice also all the plugins it says are missing. None of those are in synaptic, at least not by those names.

Or, are there other ways to get consistent multimedia in Epiphany?

---

