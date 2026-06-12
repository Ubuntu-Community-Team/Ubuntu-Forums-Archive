---
title: "Lost Desktop behaviours"
date: 2012-06-19
forum: Desktop Environments
---

### Post by brooney on 2012-06-19
Hi everyone,

I seem to have done something to my environment that has caused the Ubuntu 12.04 desktop not to behave as it used to. I believe I messed it up while I was looking at ubuntu tweak. I had installed it to see if I could control which applications showed in the application list cause I couldn't seem to get sublime text editor to show up in the list. 

While looking at Ubuntu Tweak I noticed the Janitor section and thought to myself, hey, why not clean this up. I think this caused my issues.

I now see a number of issues that I'm not sure how to fix. They may all be related but I'm not sure:

1. Icon colours in the unity bar look wrong
2. When I open the menu in the unity bar the highlight square is different
3. the popup menu in the unity bar is a pale grey now instead of transparent dark grey
4. switching between desktops is no longer smooth
5. the app switcher when using alt-tab is now grey
6. multiple instances of an application are no longer grouped into a single icon when using the app switcher
7. the desktop switcher is now pale grey instead of transparent black
8. the desktop switcher is now 3x2 instead of 6x1. can't find how to change this back.

there were a number of other preferences that i had to to reconfigure such as when activate window on mouse over, change unity icon size as it had changed to what looked like 64x64. I changed it to 32x32 using a script.

i've attached 2 screenshots of the Unity bar and menu which I hope will help describe what is happening. I couldn't get a screenshot of the switchers.

I'm not sure where to go with this. The machine is 4+ years old and has never had a re-install, just upgrades of Ubuntu over the years. Maybe it's time for a clean install but I would prefer not to as this is my work machine.

---

### Post by wilee-nilee on 2012-06-19
If you want the unity desktop set to the stock install, so you can tweak with the correct tools, run
```
alt-f2 unity --reset
```A four year old machine, work machine, I hope you have full backups and a clone of the OS's.

---

### Post by brooney on 2012-06-19
> **wilee-nilee said:**
> If you want the unity desktop set to the stock install, so you can tweak with the correct tools, run
```
alt-f2 unity --reset
```A four year old machine, work machine, I hope you have full backups and a clone of the OS's.

Thanks for the quick reply and I definitely have backups and I use virtualbox for a lot of my work so I have back ups of those too :). 

I gave that a shot and it didn't make any difference. A few other behaviours that I forgot about but just remembered:

1. it now shows a grey background at first and then loads my default workspace when i log in. the grey background hangs around for about 5-10 seconds

2. i mentioned that the switching between virtual desktops is different now. previously it would slide to the left or right but now it is just a jump to the next desktop... no nice animation.

i feel some of this, if not all, is compiz related but i've looked around in the compiz settings and haven't really found anything

---

### Post by blackflame2996 on 2012-06-20
> **brooney said:**
> 
1. it now shows a grey background at first and then loads my default workspace when i log in. the grey background hangs around for about 5-10 seconds


which desktop do you use? this happens frequently in Ubuntu 2D.

---

### Post by brooney on 2012-06-20
> **blackflame2996 said:**
> which desktop do you use? this happens frequently in Ubuntu 2D.

I was using the default Unity that came during upgrades. I'm guessing it was Unity 3D. Maybe my system has reverted to Inity 2d.

I do remember I also ran an apt-get autoremove or autoclean (it was a week ago and at my age you don't remember things :) ) I've run them in the past without any issue but maybe this time it removed some packages it shouldn't have.

I say this because one other issue I had which I solved with a hack was my virtualbox wouldn't come up anymore due to a missing lib: libGL.so.1. I found a copy on my system and symbolically linked it to /usr/local

I looked in the apt repository for a package that supplied libGL.so before I symbolically linked the file.  It came back with libgl1-mesa-swx11 but it said it needed to remove a number of packages that I need daily when I went to install it so I went the symbolic link route instead.

---

### Post by brooney on 2012-06-20
So I have confirmed that the computer was falling back to Unity 2D and I have now resolved the issue. I decided to install the package I mentioned above:
```

sudo apt-get install libgl1-mesa-swrast

```

That didn't immediately solve the issue after a reboot. I took a look at my third party drivers and noticed the graphics card was not installed again. I had re-installed it yesterday but I guess with the package install it became un-installed. I re-activated it and then rebooted and voila...Unity 3D is back baby!!

Thanks for the hints / help.

Now, I get the following when i go to run apt-get autoremove which has be a bit scared...should I be? :)
```

brooney@darla:~$ sudo apt-get autoremove
[sudo] password for brooney: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  bluez-alsa:i386 glib-networking:i386 gstreamer0.10-plugins-base:i386 gstreamer0.10-plugins-good:i386 gstreamer0.10-x:i386
  gtk2-engines:i386 gtk2-engines-murrine:i386 gtk2-engines-pixbuf:i386 gvfs:i386 gvfs-libs:i386 ibus-gtk:i386 lib32z1 libaa1:i386
  libaio1:i386 libao-common libao4:i386 libasn1-8-heimdal:i386 libatk1.0-0:i386 libaudiofile1:i386 libavc1394-0:i386 libcaca0:i386
  libcairo-gobject2:i386 libcanberra-gtk-module:i386 libcanberra-gtk0:i386 libcanberra0:i386 libcap2:i386 libcapi20-3:i386
  libcdparanoia0:i386 libcroco3:i386 libctemplate0 libcupsimage2:i386 libcurl3:i386 libdbus-glib-1-2:i386 libdrm-dev:i386
  libdv4:i386 libesd0:i386 libexif12:i386 libgail-common:i386 libgail18:i386 libgconf-2-4:i386 libgd2-xpm:i386 libgdbm3:i386
  libgettextpo0:i386 libgl1-mesa-dri:i386 libglapi-mesa:i386 libgnome-keyring0:i386 libgomp1:i386 libgphoto2-2:i386
  libgphoto2-port0:i386 libgssapi3-heimdal:i386 libgstreamer-plugins-base0.10-0:i386 libgstreamer0.10-0:i386 libgtk2.0-0:i386
  libgudev-1.0-0:i386 libhal1 libhcrypto4-heimdal:i386 libheimbase1-heimdal:i386 libheimntlm0-heimdal:i386 libhx509-5-heimdal:i386
  libibus-1.0-0:i386 libidn11:i386 libiec61883-0:i386 libieee1284-3:i386 libkms1:i386 libkrb5-26-heimdal:i386 libldap-2.4-2:i386
  libllvm3.0:i386 libltdl7:i386 libmad0:i386 libmikmod2:i386 libmpg123-0:i386 libnspr4:i386 libnss3:i386 libodbc1:i386
  libopenal1:i386 liborc-0.4-0:i386 libosmesa6 libproxy1:i386 libpulse-mainloop-glib0:i386 libpulsedsp:i386 libqt4-designer:i386
  libqt4-qt3support:i386 libqt4-scripttools:i386 libqt4-svg:i386 libqt4-test:i386 libqtwebkit4:i386 libraw1394-11:i386
  libroken18-heimdal:i386 librsvg2-2:i386 librsvg2-common:i386 librtmp0:i386 libsane:i386 libsasl2-2:i386 libsasl2-modules:i386
  libsdl-image1.2:i386 libsdl-mixer1.2:i386 libsdl-net1.2:i386 libsdl-ttf2.0-0:i386 libsdl1.2debian:i386 libshout3:i386
  libsoup-gnome2.4-1:i386 libsoup2.4-1:i386 libspeex1:i386 libsqlite3-0:i386 libssl0.9.8:i386 libssl1.0.0:i386 libstdc++5:i386
  libtag1-vanilla:i386 libtag1c2a:i386 libtdb1:i386 libtheora0:i386 libunistring0:i386 libusb-0.1-4:i386 libv4l-0:i386
  libv4lconvert0:i386 libvisual-0.4-0:i386 libvorbisfile3:i386 libwavpack1:i386 libwind0-heimdal:i386 libx11-xcb1:i386 libxaw7:i386
  libxcb-glx0:i386 libxcomposite1:i386 libxcursor1:i386 libxdamage1:i386 libxext-dev:i386 libxfixes3:i386 libxinerama1:i386
  libxmu6:i386 libxp6:i386 libxpm4:i386 libxrandr2:i386 libxslt1.1:i386 libxtst6:i386 libxxf86vm1:i386 libzip1 mesa-common-dev:i386
  nspluginviewer:i386 nspluginwrapper nvidia-settings odbcinst1debian2:i386 python-pysqlite2 screen-resolution-extra
  x11proto-xext-dev xaw3dg:i386
0 upgraded, 0 newly installed, 145 to remove and 0 not upgraded.
After this operation, 170 MB disk space will be freed.
Do you want to continue [Y/n]? 

```

---

