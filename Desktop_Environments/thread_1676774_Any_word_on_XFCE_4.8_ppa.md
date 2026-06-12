---
title: "Any word on XFCE 4.8 ppa?"
date: 2011-01-27
forum: Desktop Environments
---

### Post by slooksterpsv on 2011-01-27
I don't think that the regular 10.10 or 10.04 repos have XFCE 4.8, so I was wondering if anyone has any information on a PPA for XFCE 4.8 or that. If you could let me know, that'd be great.

---

### Post by y6FgBn)~v on 2011-01-27
[I found this one for 10.04.]("https://launchpad.net/~alexx2000/+archive/xfce")

---

### Post by slooksterpsv on 2011-01-27
Hmmm... I'll try but I thought I read for 32-bit only. I'm running 64-bit.

EDIT:

No dice, won't run, sorry it took me so long. I decided I'm going to install Xubuntu 11.04 Alpha 1 on my 80GB Partition and update it to 4.8.

I like it =D

---

### Post by lufte on 2011-01-29
Still no news? I haven't be able to find one myself, and I mean one with amd64 packages.

---

### Post by SantaFe on 2011-01-29
Didn't work for me in 32 bit Kubuntu 10.10 either. :(

---

### Post by slooksterpsv on 2011-01-30
I compiled it and got it working, but ran into a few snags, trying to get help on those snags right now.

1. I couldn't use a symbolic link for libxfconf-0.so in /lib - I had to copy it there.

2. [strike]When following the guide, I did: ./configure --prefix=/usr && make && sudo make install - in every directory, this ended up putting all the etc files into /usr/etc - I fixed that with: sudo cp -Rn /usr/etc/* /etc/ -[/strike] **FIXED** - needed to do this: ./configure --prefix=/usr --sysconfdir=/etc && make && sudo make install

3. Transparencies weren't on by default like they are in 11.04, not sure if that's a configuration modification from personal compiling to 11.04.

EDIT:

For anyone wanting to try and compile on their own, I can post a file that will compile everything in order and make the necessary changes to fix #1 and #2. You will have to just compile and install garcon, and compile and install the dependencies that aren't in the xfce48 source. (e.g. autoconf, pkg-config, etc.) 

Also I setup PKGCONFIG like so:

export PKG_CONFIG_PATH="/usr/lib/pkgconfig:/usr/bin/pkg-config"

and I didn't use the compiler options

---

### Post by slumbergod on 2011-01-30
One of the Xubuntu Devs kindly answered my question about the release of packages to enable upgrading to xfce 4.8. The reply was that they were waiting for some annoying bugs to be fixed and that adding a new PPA or updating the Xubuntu Dev PPA is something they are thinking about.

I hope they provide an option for it because I'm interested in the new Thunar now.

---

### Post by SantaFe on 2011-01-30
Found this post in the Xfce forums: [http://forum.xfce.org/viewtopic.php?id=5712](http://forum.xfce.org/viewtopic.php?id=5712)

Doesn't say if it's 32 bit or 64 bit though.  But it DOES work in my 32bit Xubuntu 10.10.

I did it by manually adding the two lines below into Synaptic.

> This PPA can be added to your system manually by copying the lines below and adding them to your system's software sources.

deb [http://ppa.launchpad.net/koshi/xfce-4.8/ubuntu](http://ppa.launchpad.net/koshi/xfce-4.8/ubuntu) maverick main 
deb-src [http://ppa.launchpad.net/koshi/xfce-4.8/ubuntu](http://ppa.launchpad.net/koshi/xfce-4.8/ubuntu) maverick main 

Signing key:
    1024R/B056DD89 (What is this?) 
Fingerprint:
    E4EC643FC995793CAC5C1C1EC81A926CB056DD89  and after I made Synaptic reload the repository list, it showed up.

Note. It still shows xfce4 as 4.6.2, but when you choose it to install, it downloads all the 4.8 files & installs them.  

May use it till the Official PPA's are released.

---

### Post by slooksterpsv on 2011-01-30
> **SantaFe said:**
> Found this post in the Xfce forums: [http://forum.xfce.org/viewtopic.php?id=5712](http://forum.xfce.org/viewtopic.php?id=5712)

Doesn't say if it's 32 bit or 64 bit though.  But it DOES work in my 32bit Xubuntu 10.10.

I did it by manually adding the two lines below into Synaptic.

 and after I made Synaptic reload the repository list, it showed up.

Note. It still shows xfce4 as 4.6.2, but when you choose it to install, it downloads all the 4.8 files & installs them.  

May use it till the Official PPA's are released.

I'll have to try that, I just  made a document on how to compile XFCE 4.8, then saw this hahaha. Oh well, it's all good =D.

EDIT: My computer, for compiling it, shows XFCE 4.8.0 - not sure if maybe they didn't update the Package information/configuration to reflect 4.8.0 - I'll try in a VM now.

EDIT 2: Or you can do: sudo apt-add-repository ppa:koshi/xfce-4.8

EDIT 3: Nope the PPA didn't work for me, it gives me the cryptic menus/... is not found.. Hmmm

---

### Post by gmargo on 2011-01-30
> **slooksterpsv said:**
> I'll have to try that, I just  made a document on how to compile XFCE 4.8, then saw this hahaha. 

Please post your document anyway.

---

### Post by slooksterpsv on 2011-01-30
Well I'm just going to post the script, you have to run it under root and it will do all the work for you:

[php]
apt-get install make gcc binutils bison m4 gdb autoconf automake libtool intltool build-essential pkg-config libgtk2.0-dev libglib2.0-dev coffeescript libstartup-notification0-dev  libgladeui-1-dev libdbus-glib-1-dev libglade2-dev liburi-perl libwnck-dev libpng12-dev libxi-dev libxrandr-dev libnotify-dev libxml-parser-perl libfreetype6-dev libjpeg62-dev libgconf2-dev libgnome-keyring-dev 
export PKG_CONFIG_PATH="/usr/lib/pkgconfig:/usr/bin/pkg-config"
mkdir -p ~/tmp/garcon-1/
cd ~/tmp/garcon-1/
wget -c http://archive.xfce.org/src/libs/garcon/0.1/garcon-0.1.5.tar.bz2
tar -xjf garcon-0.1.5.tar.bz2
cd ~/tmp/garcon-1/garcon-0.1.5
./configure --prefix=/usr --sysconfdir=/etc && make && gksudo make install
export PKG_CONFIG_PATH="/usr/lib/pkgconfig:/usr/bin/pkg-config"
mkdir -p ~/tmp/xfce48/
cd ~/tmp/xfce48
wget -c http://archive.xfce.org/xfce/4.8/fat_tarballs/xfce-4.8.tar.bz2
tar -xjf xfce-4.8.tar.bz2
cd ~/tmp/xfce48/src
for file in *.bz2 
do
 tar -xjf $file
done
cd ~/tmp/xfce48/src/xfce4-dev-tools-4.8.0
./configure --prefix=/usr --sysconfdir=/etc && make && make install
cd ../libxfce4util-4.8.1
./configure --prefix=/usr --sysconfdir=/etc && make && make install
cd ../xfconf-4.8.0
./configure --prefix=/usr --sysconfdir=/etc && make && make install
rm /lib/libxfconf-0.so && cp /usr/lib/libxfconf-0.so /lib/
cd ../libxfce4ui-4.8.0
./configure --prefix=/usr --sysconfdir=/etc && make && make install
cd ../libxfcegui4-4.8.0
./configure --prefix=/usr --sysconfdir=/etc && make && make install
cd ../exo-0.6.0
./configure --prefix=/usr --sysconfdir=/etc && make && make install
cd ../xfce4-panel-4.8.0
./configure --prefix=/usr --sysconfdir=/etc && make && make install
cd ../Thunar-1.2.0
./configure --prefix=/usr --sysconfdir=/etc && make && make install
cd ../xfce4-settings-4.8.0
./configure --prefix=/usr --sysconfdir=/etc && make && make install
cd ../xfce4-session-4.8.0
./configure --prefix=/usr --sysconfdir=/etc && make && make install
cd ../xfwm4-4.8.0
./configure --prefix=/usr --sysconfdir=/etc && make && make install
cd ../xfdesktop-4.8.0
./configure --prefix=/usr --sysconfdir=/etc && make && make install
cd ../xfce4-appfinder-4.8.0
./configure --prefix=/usr --sysconfdir=/etc && make && make install
cd ../xfce-utils-4.8.0
./configure --prefix=/usr --sysconfdir=/etc && make && make install
cd ../gtk-xfce-engine-2.8.0
./configure --prefix=/usr --sysconfdir=/etc && make && make install
[/php]

Due to make install, you have to run this as root, otherwise it won't work.

I think I fixed all the errors, I ran it, and I think it's working, still compiling but here it is.

Yup tested it works!

---

### Post by michael.conner on 2011-02-08
> **slooksterpsv said:**
> Well I'm just going to post the script, you have to run it under root and it will do all the work for you:

(code snipped)

Due to make install, you have to run this as root, otherwise it won't work.

I think I fixed all the errors, I ran it, and I think it's working, still compiling but here it is.

Yup tested it works!

Thank you! Works like a charm under 10.10.

---

### Post by glennr on 2011-03-02
This didn't work for me on 10.04 amd64.

Firstly coffeescript wasn't available, so I got it from a ppa [http://opinionated-programmer.com/2010/12/installing-coffeescript-on-debian-or-ubuntu/]("http://opinionated-programmer.com/2010/12/installing-coffeescript-on-debian-or-ubuntu/").

The build fails when building garcon:
```

make  all-recursive
make[1]: Entering directory `/home/glenn/tmp/garcon-1/garcon-0.1.5'
Making all in garcon
make[2]: Entering directory `/home/glenn/tmp/garcon-1/garcon-0.1.5/garcon'
  GEN    stamp-garcon-marshal.h
  GEN    garcon-marshal.c
make  all-am
make[3]: Entering directory `/home/glenn/tmp/garcon-1/garcon-0.1.5/garcon'
  CC     libgarcon_1_la-garcon-config.lo
In file included from /usr/include/glib-2.0/glib/gbookmarkfile.h:28,
                 from /usr/include/glib-2.0/glib.h:39,
                 from /usr/include/glib-2.0/gobject/gtype.h:26,
                 from /usr/include/glib-2.0/gobject/gboxed.h:26,
                 from /usr/include/glib-2.0/glib-object.h:25,
                 from ../garcon/garcon-config.h:28,
                 from garcon-config.c:25:
/usr/include/time.h:226: error: expected declaration specifiers or '...' before '__locale_t'

```

It also has the same error if I try to build it from the deb-src packages [http://ubuntuforums.org/showthread.php?t=1698024]("http://ubuntuforums.org/showthread.php?t=1698024")

---

### Post by lufte on 2011-03-02
There is a new repository that will provide amd64 packages for Lucid, but it is still under development.

[link]("https://launchpad.net/%7Eneuromancer85/+archive/xfce48-lucid-ppa")

---

