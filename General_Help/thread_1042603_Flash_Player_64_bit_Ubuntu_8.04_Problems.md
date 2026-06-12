---
title: "Flash Player 64 bit Ubuntu 8.04 Problems"
date: 2009-01-17
forum: General Help
---

### Post by raiderleaf on 2009-01-17
Hello,

I'm running 8.04 Ubuntu 64-bit edition and I am having one heck of a time with this Adobe Flash Plugin. Not only does the one on the website give me problems (Adobe's official) because when I download the .deb for Ubuntu 8.04+ LTS it says "incompatible architecture i386". I tried a million things across google to get it working, but to no success. I currently have installed the swf player, flashplugin-nonfree, and the gstreamer codec plugins. I get sites like youtube, raiders.com (i'm a raiders fan), and google video to work, but I can't get sites like nfl.com to pop up any of the videos period, and the bar at the top that tells you who is playing who doesn't load. Any solutions? The odd thing is on NFL.com as soon as I click one of the videos to the right that just shows a small screenshot, it plays in the big box to the left where nothing currently is even though there is something supposed to be there... Any thoughts?

Thanks,
raiderleaf

---

### Post by 2hot6ft2 on 2009-01-17
> **raiderleaf said:**
> Hello,

I'm running 8.04 Ubuntu 64-bit edition and "incompatible architecture i386".Looks like you answered your own question there you're trying to install the 32 bit package on a 64 bit OS.
If you just want the flash, Java and other multimedia stuff here's the easy way.
Put this in a terminal and hit Enter
Applications>Accessories>Terminal

```
sudo apt-get install ubuntu-restricted-extras

```
Then your password and Enter (your password will not be displayed)

It will fix that as well as other missing multimedia you haven't found out about yet.

When it gets to the agreement hit Tab then Enter to accept the Java agreement.
All done and you don't have to worry about getting the right version as it will do it automatically.

If you want a specific version then just be sure to get the 64 bit package.

---

### Post by oldos2er on 2009-01-17
[http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz)

---

### Post by raiderleaf on 2009-01-17
> **2hot6ft2 said:**
> Looks like you answered your own question there you're trying to install the 32 bit package on a 64 bit OS.
If you just want the flash, Java and other multimedia stuff here's the easy way.
Put this in a terminal and hit Enter
Applications>Accessories>Terminal

```
sudo apt-get install ubuntu-restricted-extras

```
Then your password and Enter (your password will not be displayed)

It will fix that as well as other missing multimedia you haven't found out about yet.

When it gets to the agreement hit Tab then Enter to accept the Java agreement.
All done and you don't have to worry about getting the right version as it will do it automatically.

If you want a specific version then just be sure to get the 64 bit package.

I have long already tried this method unfortunately, and it did not work at all. :-(

---

### Post by raiderleaf on 2009-01-17
> **oldos2er said:**
> [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz)

I did untar that file and i tried copying it in usr/lib/mozilla/plugins and it went in there, but should it have gone in usr/lib/mozilla-firefox/plugins? I tried to copy it in there as well but it won't take.

---

### Post by oldos2er on 2009-01-17
> **raiderleaf said:**
> I did untar that file and i tried copying it in usr/lib/mozilla/plugins and it went in there, but should it have gone in usr/lib/mozilla-firefox/plugins? I tried to copy it in there as well but it won't take.

 I don't honestly know. Mine's only in /usr/lib/mozilla/plugins .

---

### Post by raiderleaf on 2009-01-19
> **oldos2er said:**
> I don't honestly know. Mine's only in /usr/lib/mozilla/plugins .

Well mine is in there... any clues?

---

### Post by theWrkncacnter on 2009-01-19
If at all possible, use Synaptic. I have ubuntu 64 bit, and use flash.
Make sure you have the universe and multiverse repositories enabled, then search for "flash" within Synaptic and install the flash plugin non-free. Hope that helps!
Edit: whoops, you already have that installed -- I hope you can figure it out. Good luck!

---

### Post by fooman on 2009-01-19
> **raiderleaf said:**
> I did untar that file and i tried copying it in usr/lib/mozilla/plugins and it went in there, but should it have gone in usr/lib/mozilla-firefox/plugins? I tried to copy it in there as well but it won't take.

you should only need to copy it to /home/<user name>/.mozilla/plugins

uninstall any instances of flash/gnash that you previously installed using synaptic.

---

### Post by raiderleaf on 2009-01-21
> **fooman said:**
> you should only need to copy it to /home/<user name>/.mozilla/plugins

uninstall any instances of flash/gnash that you previously installed using synaptic.

The directory to which you have referenced does not exist on my machine. See terminal below.

[email]usrname@usrname-desktop:~/.mozill[/email]a$ ls -a
.  ..  appreg  default  extensions  firefox
[email]usrname@usrname-desktop:~/.mozill[/email]a$ cd plugins
bash: cd: plugins: No such file or directory
[email]usrname@usrname-desktop:~/.mozill[/email]a$ cd extensions/
[email]usrname@usrname-desktop:~/.mozill[/email]a/extensions$ ls -a
.  ..  {ec8030f7-c20a-464f-9b0e-13a3a9e97384}
[email]usrname@usrname-desktop:~/.mozill[/email]a/extensions$ cd ..
[email]usrname@usrname-desktop:~/.mozill[/email]a$ cd firefox/
[email]usrname@usrname-desktop:~/.mozill[/email]a/firefox$ ls -a
.  ..  5mpc41ud.default  pluginreg.dat  profiles.ini
[email]usrname@usrname-desktop:~/.mozill[/email]a/firefox$

---

### Post by fooman on 2009-01-21
create it.  you can open your home folder,  browse to the .mozilla folder,  right click an empty area and choose "create folder"....name it "plugins" (no quotes)

or in a termnal:

```
mkdir ~/.mozilla/plugins
```

then copy the libflashplayer.so file there.

hope that helps.

---

### Post by raiderleaf on 2009-01-21
> **fooman said:**
> create it.  you can open your home folder,  browse to the .mozilla folder,  right click an empty area and choose "create folder"....name it "plugins" (no quotes)

or in a termnal:

```
mkdir ~/.mozilla/plugins
```

then copy the libflashplayer.so file there.

hope that helps.

Well I went and tried that and sad to say there are no changes. See, the thing about this all is that some sites perform fine, it just happens to be that the sites I need it to work on fail, like NFL.com and MSNBC Video. I don't understand how that is happening. Is there anyway to manually patch it for those specific sites? I'd really love a general fix, but it is getting really annoying having to boot into another OS that can play embedded media files or access NFL.com.

---

