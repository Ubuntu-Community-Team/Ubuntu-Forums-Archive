---
title: "How does one build from source?"
date: 2009-01-08
forum: General Help
---

### Post by KingAlanI on 2009-01-08
The application-install process is one of the big differences I notice between Ubuntu and Windows.

The package manager makes it easy to install stuff *that is listed in the package manager*...

However, would I have to build from source to install something that isn't listed in the package manager? The application's developers may or may not make a package available...

Source often comes in the form of .tar.gz files, does it not?
That's a form of archive/compression from what I understand. It presumably would be straightforward to unarchive/uncompress, but what would I do with the resultant files?

I don;t need to build my own apps, I am interested in building other peoples' apps.

I don't necessarily need a Free Software compiler/whatever; I just want one that works in my linux environment.

[http://magicseteditor.sourceforge.net](http://magicseteditor.sourceforge.net) is a target utility I have in mind; I have liked its Windows incarnation, maybe this could at the least be  a test case.

---

### Post by leg on 2009-01-08
[Linux documentation project]("http://tldp.org/HOWTO/Software-Building-HOWTO.html") has a great howto for it.

If it isn't in synaptic then you don't necessarily need to build it. If you can find somewhere that maintains a .deb or a rpm for the software you could use that.

---

### Post by iamnotloggedon on 2010-11-06
Sorry to jump in here but I'm having a similar problem with Magic Set Editor. It appears the program has installed but now when I try to run the the file via the Terminal (running as root of course) I get this error: 

/home/jack/Downloads/magicseteditor/program/magicseteditor: error while loading shared libraries: libwx_gtk2u_richtext-2.8.so.0: cannot open shared object file: No such file or directory

I know I need to get that library that it says is missing but where can I find it? I've already checked the Ubuntu website for its list of Lucid libraries and not one of them begin with "libwx" and I haven't had much luck searching either Bing or UbuntuForums.

---

### Post by Xinerama on 2010-11-06
A couple of tips I can give you guys.
Whenever you download your source, try to unpack it in /usr/local that way you keep everything together.  Also create a directory called /usr/local/tarballs and move your tar.gz files there after you've unpacked them.
Read the readme files as they are very helpful.
After installing your programs make sure you run ldconfig.

That's it from me.  It's been a while since I built anything from source personally.
I don't have the programming knowledge that most do so I say good luck to you, because trying to resolve dependency issues and version differences is a pain sometimes.  
Honestly, if your not up for the challenge and have the RAM and HDD space you could just try and install the software on Windows using VirtualBox. :(

---

### Post by oldos2er on 2010-11-06
I ran **apt-cache search libwx** and got a lot of hits. Check your Software Sources to make sure you have all repositories enabled. 

[http://packages.ubuntu.com/search?keywords=libwx&searchon=names&suite=lucid&section=all](http://packages.ubuntu.com/search?keywords=libwx&searchon=names&suite=lucid&section=all)

---

### Post by iamnotloggedon on 2010-11-07
> **oldos2er said:**
> I ran **apt-cache search libwx** and got a lot of hits. Check your Software Sources to make sure you have all repositories enabled. 

[http://packages.ubuntu.com/search?keywords=libwx&searchon=names&suite=lucid&section=all](http://packages.ubuntu.com/search?keywords=libwx&searchon=names&suite=lucid&section=all)

Well I ran the same code and got this:

> libwx-perl - interface to wxWidgets cross-platform GUI toolkit
libwx-perl-datawalker-perl - Perl data structure browser
libwx-perl-dialog-perl - abstract dialog class for simple dialog creation
libwx-perl-processstream-perl - access IO of external processes via events (Wx:Perl module)
libwx11-0 - library to manage xlib
libwx11-0-dbg - library to manage xlib - debug
libwx11-dev - library to manage xlib - devel
libwxsmithlib0 - wxSmith shared library (wxSmith is a Code::Blocks plugin for RAD GUI editing)
libwxsmithlib0-dev - wxSmith development files
libwxsvg-dev - C++ library to create, manipulate and render SVG files (devel)
libwxsvg0 - C++ library to create, manipulate and render SVG files
libwxbase2.6-0 - wxBase library (runtime) - non-GUI support classes of wxWidgets toolkit
libwxbase2.6-dbg - wxBase library (debug) - non-GUI support classes of wxWidgets toolkit
libwxbase2.6-dev - wxBase library (development) - non-GUI support classes of wxWidgets toolkit
libwxbase2.8-0 - wxBase library (runtime) - non-GUI support classes of wxWidgets toolkit
libwxbase2.8-dbg - wxBase library (debug) - non-GUI support classes of wxWidgets toolkit
libwxbase2.8-dev - wxBase library (development) - non-GUI support classes of wxWidgets toolkit
libwxgtk2.6-0 - wxWidgets Cross-platform C++ GUI toolkit (GTK+ runtime)
libwxgtk2.6-dbg - wxWidgets Cross-platform C++ GUI toolkit (GTK+ development)
libwxgtk2.6-dev - wxWidgets Cross-platform C++ GUI toolkit (GTK+ development)
libwxgtk2.8-0 - wxWidgets Cross-platform C++ GUI toolkit (GTK+ runtime)
libwxgtk2.8-dbg - wxWidgets Cross-platform C++ GUI toolkit (GTK+ debugging)
libwxgtk2.8-dev - wxWidgets Cross-platform C++ GUI toolkit (GTK+ development)
but the library missing according to MSE isn't in there. I can't remember if I posted the whole thing or not already but here's the code anyways:

> Jack@ubuntu:~$ /home/jack/Downloads/magicseteditor/program/magicseteditor
/home/jack/Downloads/magicseteditor/program/magicseteditor: error while loading shared libraries: libwx_gtk2u_richtext-2.8.so.0: cannot open shared object file: No such file or directory
I'm not entirely sure how to enable, disable or check on the status of repositories. Also it may be worth mentioning that although I run Kubuntu I have Synaptic Package Manager installed and tend to use it more often than KPackage Manager.

-Jack L.

---

### Post by oldos2er on 2010-11-07
In Synaptic, check menus Settings, Repositories.

Looks like you need to install libwxgtk2.8-dev if you haven't already.

---

### Post by iamnotloggedon on 2010-11-07
> **oldos2er said:**
> In Synaptic, check menus Settings, Repositories.

Looks like you need to install libwxgtk2.8-dev if you haven't already.

I have libwxgtk2.8-dev installed and went under settings to repositories. The only thing I saw that may be it was under "Other Software" the last two items weren't checked, they both read akirad repository sources-Main. and after their URLs they both said "(Source Code)" (sorry, it won't let me copy and paste). I tried checking them but when I refreshed Synaptic I got an error message saying it couldn't download all repository indexes. The box inside read:

> Failed to fetch cdrom://Kubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100427)/dists/lucid/main/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Kubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100427)/dists/lucid/restricted/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch [http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages.gz](http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages.gz)  404  Not Found [IP: 212.72.53.130 80]
Some index files failed to download, they have been ignored, or old ones used instead.

I'm not sure what to do about this or if it's even related at all. I do have an AMD 64 processor (although it is a 32-bit processor) if that helps any.

---

