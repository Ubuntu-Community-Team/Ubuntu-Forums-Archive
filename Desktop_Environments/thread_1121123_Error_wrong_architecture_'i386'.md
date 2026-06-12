---
title: "Error: wrong architecture 'i386'"
date: 2009-04-09
forum: Desktop Environments
---

### Post by D@RKKIN6 on 2009-04-09
Hi 

Does anyone know what this error mean? Error: wrong architecture 'i386'

I get it always when I try to install something with Package Installer.
I've tried to install Flash player, Opera browser, ...
but I always get this error.

---

### Post by taurus on 2009-04-09
Are you running i686 (32bit) or x86_64 (64bit)?

```
uname -m
```

---

### Post by Michael.Godawski on 2009-04-09
hi D@RKKIN6,

this means you try to install 32-bit applications on a 64 bit system. 
Check which version of Ubuntu you have installed with

```
uname -a
lsb_release -a
```

---

### Post by SuperSonic4 on 2009-04-09
I'm guessing it would be 64bit from the title of the post

Flash can be installed by following the following ```
32/64-bit Users: Alternatively, 32-bit users can download the Tar archive from the same link provided above and follow my instructions below. If you're a 64-bit Ubuntu user, download the Tar archive of the 64-bit Flash Player plug-in from the bottom of [this page]("http://labs.adobe.com/downloads/flashplayer10.html") to your desktop.

Once downloaded, simply open the Tar archive, look for a file named "libflashplayer.so", copy that file to your desktop, then both 32-bit and 64-bit users execute the following command in the terminal:

sudo mkdir /usr/lib/flashplugin-nonfree && sudo cp -f ~/Desktop/libflashplayer.so /usr/lib/flashplugin-nonfree/ && sudo ln -sf /usr/lib/flashplugin-nonfree/libflashplayer.so /etc/alternatives/firefox-flashplugin && sudo ln -sf /etc/alternatives/firefox-flashplugin /usr/lib/firefox-addons/plugins/flashplayer-alternative.so
```

Source: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by doorknob60 on 2009-04-09
For flash on 64 bit download [this]("http://labs.adobe.com/downloads/flashplayer10.html") and then extract it either to /usr/lib/mozilla/plugins/ (need to use sudo in terminal or gksudo nautilus) or to $HOME/.mozilla/plugins (need to use terminal or press ctrl+h to get hiddden folders to show up in nautilus). I use that Flash Plugin and it works great.

There's also 64 bit (amd64 or x86_64 it might be called) versions of Opera, so download that instead.

In general, if you're given the option, download amd64 versions of any software, otherwise you'll have to mess with forcing architectures and using getlibs, but that's rare since 99% of everything you use should be in the repositories.

---

### Post by dcstar on 2009-04-09
> **doorknob60 said:**
> ........
In general, if you're given the option, download amd64 versions of any software, otherwise you'll have to mess with forcing architectures and using getlibs, but that's rare since 99% of everything you use should be in the repositories.

Unless people have added 3rd party repositories - as so many "helpful" items of advice out there continually say to do....   :-(

---

### Post by vbulash on 2009-04-10
> **D@RKKIN6 said:**
> Hi 

Does anyone know what this error mean? Error: wrong architecture 'i386'

I get it always when I try to install something with Package Installer.
I've tried to install Flash player, Opera browser, ...
but I always get this error.

For some programs 64-bit version doesn't exist yet - try to ask Adobe about 64-bit version of Adobe Reader ;-)
But it is possible to force install 32-bit deb on 64-bit system by:

```
sudo dpkg -i --force-architecture deb-package-32bit-file-name
```

---

### Post by D@RKKIN6 on 2009-04-10
I've installed it using Wubi.exe on windows Vista, so it downloaded and installed it automaticaly. 
So I have to open Terminal
and write down
uname -a 
or
lsb_release -a
to see wich version I have installed
and this code
sudo dpkg -i --force-architecture deb-package-32bit-file-name
e.g.
sudo dpkg -i --force-architecture deb-package-32bit-[COLOR="Red"]libflashplayer.so[/COLOR]
let me install 32bit program on a 64bit Operating System?
Thanks you all for your help
Now I have to try it when I go home :p

---

### Post by D@RKKIN6 on 2009-04-10
after writing uname -a I've got this message shown
So my operating system is 64bit version.

Linux ubuntu 2.6.27-11-generic #1 SMP Wed Apr 1 20:5:41 UTC 2009 x86_64 GNU/Linux

---

### Post by taurus on 2009-04-10
If you want to run 32bit apps in a 64bit environment, you need to install the ia32-libs package.

---

### Post by D@RKKIN6 on 2009-04-10
I found another sollution

1)Start Windows Vista
2)Remove Ubuntu complete
3)Go to [www.ubuntu.com](www.ubuntu.com)
4)Download Ubuntu 8.10 32bit version iso file
5)Open Iso reader
6)Open Ubuntu 8.10 32bit version iso file
7)Install Wubi.exe

Now I've a 32bit Ubuntu 8.10, so I've installed Flash without problem and
other software is also going wel ;)

---

