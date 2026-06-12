---
title: "got kmplayer installed"
date: 2005-11-26
forum: Desktop Environments
---

### Post by zojas on 2005-11-26
This all started as a quest to play the videos on compfused.com on my kubuntu workstation. They seem to be a mixture of quicktime and wmv (windows media files). it's been a long road, but now I finally have kmplayer installed and working. 

each individual step I list below is easy, it's just that there are a lot of steps.

first step, is to enable all the non-free libraries for playing video and sound, and installing mplayer and realplayer. follow the directions here:

[https://wiki.ubuntu.com/RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats")

now you'll have an mplayer which you can run from the command line, but I wanted the mouse-click convenience of kmplayer.

so I ended up making .deb files for kmplayer. before you run screaming, the hard work is already done, because kmplayer ships with the files needed to build a .deb, all we have to do is run a few programs. 

basically, download the kmplayer source tarball from [http://kmplayer.kde.org/download.php]("http://kmplayer.kde.org/download.php"). then you will follow the directions at [http://ubuntuforums.org/showthread.php?t=51003]("http://ubuntuforums.org/showthread.php?t=51003"), except that all the hard work (writing all the files in the debian/ directory) is already done. 

I needed to install a few dependencies on my system. here's a transcript of the apt-get commands I used to get the dependencies of the .deb tools and kmplayer itself installed:

```

sudo apt-get install build-essential dh-make debhelper devscripts
sudo apt-get install fakeroot
sudo apt-get install kdelibs4-dev libxine-dev 
sudo apt-get install libgstreamer0.8-dev libgstreamer-plugins0.8-dev

```

then to create the .deb files, follow the howto (again, it's [http://ubuntuforums.org/showthread.php?t=51003]("http://ubuntuforums.org/showthread.php?t=51003")) and set up your directory structure as they recommend. then, this is straight out of the howto:
```

dpkg-buildpackage -rfakeroot

```

that ended up giving me 6 .deb files:

```

kmplayer-app_0.9.1_i386.deb
kmplayer-doc_0.9.1_i386.deb
kmplayer-i18n_0.9.1_i386.deb
kmplayer-lib_0.9.1_i386.deb
kmplayer-plugin_0.9.1_i386.deb
kmplayer_0.9.1_all.deb

```

which I installed using this command:

```

sudo dpkg -i *.deb

```

Finally, I opened a konquer window, went to konqueror settings, the file associations item, then verified that all the video types (that aren't handled by realplayer that is) have kmplayer at the top of the list of the players to use.

now I'm able to see any of the videos at [http://compfused.com/]("http://compfused.com/") in an embedded player in konqueror just by clicking. :cool:

---

### Post by gamma on 2006-01-25
Just used this method, and have to say... great guide!

---

### Post by zojas on 2006-01-25
thanks. :)

---

### Post by sal on 2006-01-25
[QUOTE=zojas]This all started as a quest to play the videos on compfused.com on my kubuntu workstation. They seem to be a mixture of quicktime and wmv (windows media files). it's been a long road, but now I finally have kmplayer installed and working. 

each individual step I list below is easy, it's just that there are a lot of steps.

first step, is to enable all the non-free libraries for playing video and sound, and installing mplayer and realplayer. follow the directions here:

[https://wiki.ubuntu.com/RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats")

now you'll have an mplayer which you can run from the command line, but I wanted the mouse-click convenience of kmplayer.

so I ended up making .deb files for kmplayer. before you run screaming, the hard work is already done, because kmplayer ships with the files needed to build a .deb, all we have to do is run a few programs. 

basically, download the kmplayer source tarball from [http://kmplayer.kde.org/download.php]("http://kmplayer.kde.org/download.php"). then you will follow the directions at [http://ubuntuforums.org/showthread.php?t=51003]("http://ubuntuforums.org/showthread.php?t=51003"), except that all the hard work (writing all the files in the debian/ directory) is already done. 

I needed to install a few dependencies on my system. here's a transcript of the apt-get commands I used to get the dependencies of the .deb tools and kmplayer itself installed:

```

sudo apt-get install build-essential dh-make debhelper devscripts
sudo apt-get install fakeroot
sudo apt-get install kdelibs4-dev libxine-dev 
sudo apt-get install libgstreamer0.8-dev libgstreamer-plugins0.8-dev

```

then to create the .deb files, follow the howto (again, it's [http://ubuntuforums.org/showthread.php?t=51003]("http://ubuntuforums.org/showthread.php?t=51003")) and set up your directory structure as they recommend. then, this is straight out of the howto:
```

dpkg-buildpackage -rfakeroot

```

that ended up giving me 6 .deb files:

```

kmplayer-app_0.9.1_i386.deb
kmplayer-doc_0.9.1_i386.deb
kmplayer-i18n_0.9.1_i386.deb
kmplayer-lib_0.9.1_i386.deb
kmplayer-plugin_0.9.1_i386.deb
kmplayer_0.9.1_all.deb

```

which I installed using this command:

```

sudo dpkg -i *.deb

```

Finally, I opened a konquer window, went to konqueror settings, the file associations item, then verified that all the video types (that aren't handled by realplayer that is) have kmplayer at the top of the list of the players to use.

now I'm able to see any of the videos at [http://compfused.com/]("http://compfused.com/") in an embedded player in konqueror just by clicking. :cool:[/QUOTE]


is it posable that you could upload the packages for us?

---

### Post by zojas on 2006-01-25
I don't really want to upload them. give it a try yourself though, it's not very hard!

---

### Post by sal on 2006-01-25
[QUOTE=zojas]I don't really want to upload them. give it a try yourself though, it's not very hard![/QUOTE]

don't worry, i just found the debs in some chechz kubuntu site (go google!),
anyway, i'll upload them in the morning, then come back here and pass out the link to them.

---

### Post by Pekkalainen on 2006-01-25
Please upload debs, no offence but I didnt understand much of the instructions, what part of the deb guide am I supposed to follow the first time around? And later what other part?  :confused:

---

### Post by sal on 2006-01-25
[QUOTE=Pekkalainen]Please upload debs, no offence but I didnt understand much of the instructions, what part of the deb guide am I supposed to follow the first time around? And later what other part?  :confused:[/QUOTE]

i'm going to upload the debs in the morning.
check tomorrow afternoon.

---

### Post by Pekkalainen on 2006-01-25
Great! :D

---

### Post by sal on 2006-01-26
[QUOTE=Pekkalainen]Great! :D[/QUOTE]

here is the link to all the debs rolled into a tarball:
[http://mysite.verizon.net/vze1ui63/debs/kmplayer.0.9.1a.tar.gz](http://mysite.verizon.net/vze1ui63/debs/kmplayer.0.9.1a.tar.gz)

just download and extract the debs

---

### Post by Pekkalainen on 2006-01-26
Thanks a bunch! The debs work perfectly :D

---

### Post by nicky75 on 2006-01-27
I have a problem, when I go to watch a movie, kmplayer tell me "player mplayer buffering" when arrive until 6% and then tell me "player mplayer not running". I have installed mplayer and in Firefox with mplayerplug-in works fine :confused:

---

### Post by Neo Ex on 2006-01-27
Go in the preferences of KMplayer -> General Options -> Output -> X11Shm.
I had the same problem and I've solved with this method.

---

### Post by nicky75 on 2006-01-27
Thank you :) Now I can watch well, but with mplayer I listen the voice like Donal duck, with Xine is all ok...

---

