---
title: "Need help installing steam dependancies"
date: 2013-03-15
forum: Gaming &amp; Leisure
---

### Post by mellery on 2013-03-15
I need help getting steam to run on my laptop please.  I'm getting the following error

```
Steam needs to install these additional packages: 
	libgl1-mesa-dri:i386, libgl1-mesa-glx:i386, libc6:i386
[sudo] password for mike: 
...................................................................................................................................................................................
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libgl1-mesa-dri:i386 : Depends: libdrm-intel1:i386 (>= 2.4.38) but it is not going to be installed
                        Depends: libdrm-nouveau2:i386 (>= 2.4.34) but it is not going to be installed
                        Depends: libdrm-radeon1:i386 (>= 2.4.31) but it is not going to be installed
                        Depends: libdrm2:i386 (>= 2.4.3) but it is not going to be installed
 libgl1-mesa-glx:i386 : Depends: libdrm2:i386 (>= 2.3.1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
Press return to continue: 

```

But under synaptic I don't see any broken packages and trying to install those packages gives similar errors

I'm running up to date 12.10
"Linux mike-laptop 3.5.0-25-generic #39-Ubuntu SMP Mon Feb 25 18:26:58 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux"

How can I fix steam?  Thanks

---

### Post by Perfect Storm on 2013-03-15
Install 'ia32-libs'.

```
sudo apt-get install ia32-libs
```

---

### Post by mellery on 2013-03-15
> **Artificial Intelligence said:**
> Install 'ia32-libs'.

```
sudo apt-get install ia32-libs
```

I get the following error when trying that

```
mike@mike-laptop:~$ sudo apt-get install ia32-libs
[sudo] password for mike: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 ia32-libs : Depends: ia32-libs-multiarch
E: Unable to correct problems, you have held broken packages.
mike@mike-laptop:~$ 

```

---

### Post by mellery on 2013-03-15
and then this error

```
mike@mike-laptop:~$ sudo apt-get install ia32-libs-multiarch
[sudo] password for mike: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 ia32-libs-multiarch:i386 : Depends: gstreamer0.10-plugins-good:i386 but it is not going to be installed
                            Depends: gtk2-engines:i386 but it is not going to be installed
                            Depends: gtk2-engines-murrine:i386 but it is not going to be installed
                            Depends: gtk2-engines-pixbuf:i386 but it is not going to be installed
                            Depends: gtk2-engines-oxygen:i386 but it is not going to be installed
                            Depends: ibus-gtk:i386 but it is not going to be installed
                            Depends: libcanberra-gtk-module:i386 but it is not going to be installed
                            Depends: libgail-common:i386 but it is not going to be installed
                            Depends: libglu1-mesa:i386 but it is not going to be installed
                            Depends: libgtk2.0-0:i386 but it is not going to be installed
                            Depends: libqt4-opengl:i386 but it is not going to be installed
                            Depends: librsvg2-common:i386 but it is not going to be installed
                            Recommends: libgl1-mesa-glx:i386 but it is not going to be installed
                            Recommends: libgl1-mesa-dri:i386 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
mike@mike-laptop:~$ 

```

---

### Post by Perfect Storm on 2013-03-15
```
sudo apt-get update && sudo apt-get upgrade
sudo aptitude install ia32-libs-multiarch
```

---

### Post by mellery on 2013-03-15
I'm still getting the error

```
mike@mike-laptop:~$ sudo aptitude install ia32-libs-multiarch
Note: selecting "ia32-libs-multiarch:i386" instead of the
      virtual package "ia32-libs-multiarch"
The following NEW packages will be installed:
  bluez-alsa:i386{a} gcc-4.7-base:i386{a} glib-networking:i386{a} gstreamer0.10-plugins-base:i386{a} 
  gstreamer0.10-plugins-good:i386{a} gstreamer0.10-x:i386{a} gtk2-engines:i386{a} gtk2-engines-murrine:i386{a} 
  gtk2-engines-oxygen:i386{a} gtk2-engines-pixbuf:i386{a} gvfs:i386{a} gvfs-libs:i386{a} ia32-libs-multiarch:i386 
  ibus-gtk:i386{a} libaa1:i386{a} libacl1:i386{a} libaio1:i386{a} libao4:i386{a} libasn1-8-heimdal:i386{a} 
  libasound2:i386{a} libasound2-plugins:i386{a} libasyncns0:i386{a} libatk1.0-0:i386{a} libattr1:i386{a} libaudio2:i386{a} 
  libaudiofile1:i386{a} libavahi-client3:i386{a} libavahi-common-data:i386{a} libavahi-common3:i386{a} libavc1394-0:i386{a} 
  libbz2-1.0:i386{a} libc6:i386{a} libcaca0:i386{a} libcairo-gobject2:i386{ab} libcairo2:i386{ab} 
  libcanberra-gtk-module:i386{a} libcanberra-gtk0:i386{a} libcanberra0:i386{a} libcap2:i386{a} libcapi20-3:i386{a} 
  libcdparanoia0:i386{a} libcomerr2:i386{a} libcroco3:i386{a} libcups2:i386{a} libcupsimage2:i386{a} libcurl3:i386{a} 
  libdatrie1:i386{a} libdb5.1:i386{a} libdbus-1-3:i386{a} libdbus-glib-1-2:i386{a} libdrm-intel1:i386{ab} 
  libdrm-nouveau2:i386{ab} libdrm-radeon1:i386{ab} libdrm2:i386{ab} libdv4:i386{a} libesd0:i386{a} libexif12:i386{a} 
  libexpat1:i386{a} libffi6:i386{a} libflac8:i386{a} libfontconfig1:i386{a} libfreetype6:i386{a} libgail-common:i386{a} 
  libgail18:i386{a} libgcc1:i386{a} libgconf-2-4:i386{a} libgcrypt11:i386{a} libgd2-xpm:i386{a} libgdbm3:i386{a} 
  libgdk-pixbuf2.0-0:i386{a} libgettextpo0:i386{a} libgl1-mesa-dri:i386{a} libgl1-mesa-glx:i386{a} libglapi-mesa:i386{a} 
  libglib2.0-0:i386{a} libglu1-mesa:i386{a} libgnome-keyring0:i386{a} libgnutls26:i386{a} libgpg-error0:i386{a} 
  libgphoto2-2:i386{a} libgphoto2-port0:i386{a} libgpm2:i386{a} libgssapi-krb5-2:i386{a} libgssapi3-heimdal:i386{a} 
  libgstreamer-plugins-base0.10-0:i386{a} libgstreamer0.10-0:i386{a} libgtk2.0-0:i386{a} libgudev-1.0-0:i386{a} 
  libhcrypto4-heimdal:i386{a} libheimbase1-heimdal:i386{a} libheimntlm0-heimdal:i386{a} libhx509-5-heimdal:i386{a} 
  libibus-1.0-0:i386{a} libice6:i386{a} libidn11:i386{a} libiec61883-0:i386{a} libieee1284-3:i386{a} 
  libjack-jackd2-0:i386{a} libjasper1:i386{a} libjbig0:i386{a} libjpeg-turbo8:i386{a} libjpeg8:i386{a} libjson0:i386{a} 
  libk5crypto3:i386{a} libkeyutils1:i386{a} libkrb5-26-heimdal:i386{a} libkrb5-3:i386{a} libkrb5support0:i386{a} 
  liblcms1:i386{a} libldap-2.4-2:i386{a} libllvm3.1:i386{a} libltdl7:i386{a} liblzma5:i386{a} libmad0:i386{a} 
  libmikmod2:i386{a} libmng1:i386{a} libmpg123-0:i386{a} libmysqlclient18:i386{a} libncurses5:i386{a} libncursesw5:i386{a} 
  libnspr4:i386{a} libnss3:i386{a} libodbc1:i386{a} libogg0:i386{a} libopenal1:i386{a} liborc-0.4-0:i386{a} 
  libp11-kit0:i386{a} libpango1.0-0:i386{a} libpciaccess0:i386{a} libpcre3:i386{a} libpixman-1-0:i386{a} libpng12-0:i386{a} 
  libproxy1:i386{a} libpulse-mainloop-glib0:i386{a} libpulse0:i386{a} libpulsedsp:i386{a} libqt4-dbus:i386{a} 
  libqt4-declarative:i386{a} libqt4-designer:i386{a} libqt4-network:i386{a} libqt4-opengl:i386{a} libqt4-qt3support:i386{a} 
  libqt4-script:i386{a} libqt4-scripttools:i386{a} libqt4-sql:i386{a} libqt4-sql-mysql:i386{a} libqt4-svg:i386{a} 
  libqt4-test:i386{a} libqt4-xml:i386{a} libqt4-xmlpatterns:i386{a} libqtcore4:i386{a} libqtgui4:i386{a} 
  libqtwebkit4:i386{a} libraw1394-11:i386{a} libroken18-heimdal:i386{a} librsvg2-2:i386{a} librsvg2-common:i386{a} 
  librtmp0:i386{a} libsamplerate0:i386{a} libsane:i386{a} libsasl2-2:i386{a} libsasl2-modules:i386{a} 
  libsdl-image1.2:i386{a} libsdl-mixer1.2:i386{a} libsdl-net1.2:i386{a} libsdl-ttf2.0-0:i386{a} libsdl1.2debian:i386{a} 
  libselinux1:i386{a} libshout3:i386{a} libslang2:i386{a} libsm6:i386{a} libsndfile1:i386{a} libsoup-gnome2.4-1:i386{a} 
  libsoup2.4-1:i386{a} libspeex1:i386{a} libspeexdsp1:i386{a} libsqlite3-0:i386{a} libssl0.9.8:i386{a} libssl1.0.0:i386{a} 
  libstdc++5:i386{a} libstdc++6:i386{a} libtag1-vanilla:i386{a} libtag1c2a:i386{a} libtasn1-3:i386{a} libtdb1:i386{a} 
  libthai0:i386{a} libtheora0:i386{a} libtiff5:i386{a} libtinfo5:i386{a} libtxc-dxtn-s2tc0:i386{a} libudev0:i386{a} 
  libunistring0:i386{a} libusb-0.1-4:i386{a} libusb-1.0-0:i386{a} libuuid1:i386{a} libv4l-0:i386{a} libv4lconvert0:i386{a} 
  libvisual-0.4-0:i386{a} libvisual-0.4-plugins:i386{a} libvorbis0a:i386{a} libvorbisenc2:i386{a} libvorbisfile3:i386{a} 
  libwavpack1:i386{a} libwebp2:i386{a} libwind0-heimdal:i386{a} libwrap0:i386{a} libx11-6:i386{a} libx11-xcb1:i386{a} 
  libxau6:i386{a} libxaw7:i386{a} libxcb-glx0:i386{a} libxcb-render0:i386{a} libxcb-shm0:i386{a} libxcb1:i386{a} 
  libxcomposite1:i386{a} libxcursor1:i386{a} libxdamage1:i386{a} libxdmcp6:i386{a} libxext6:i386{a} libxfixes3:i386{a} 
  libxft2:i386{a} libxi6:i386{a} libxinerama1:i386{a} libxml2:i386{a} libxmu6:i386{a} libxp6:i386{a} libxpm4:i386{a} 
  libxrandr2:i386{a} libxrender1:i386{a} libxslt1.1:i386{a} libxss1:i386{a} libxt6:i386{a} libxtst6:i386{a} libxv1:i386{a} 
  libxxf86vm1:i386{a} odbcinst1debian2:i386{a} xaw3dg:i386{a} zlib1g:i386{a} 
0 packages upgraded, 238 newly installed, 0 to remove and 0 not upgraded.
Need to get 71.9 MB/76.7 MB of archives. After unpacking 237 MB will be used.
The following packages have unmet dependencies:
 libdrm-nouveau2 : Breaks: libdrm-nouveau2:i386 (!= 2.4.40-0ubuntu0~quantal5.2) but 2.4.40-0ubuntu0~quantal5.1 is to be installed.
 libdrm-nouveau2:i386 : Breaks: libdrm-nouveau2 (!= 2.4.40-0ubuntu0~quantal5.1) but 2.4.40-0ubuntu0~quantal5.2 is installed.
 libcairo-gobject2 : Breaks: libcairo-gobject2:i386 (!= 1.12.4-0ubuntu0~quantal15.2) but 1.12.4-0ubuntu0~quantal15.1 is to be installed.
 libcairo-gobject2:i386 : Breaks: libcairo-gobject2 (!= 1.12.4-0ubuntu0~quantal15.1) but 1.12.4-0ubuntu0~quantal15.2 is installed.
 libdrm-radeon1 : Breaks: libdrm-radeon1:i386 (!= 2.4.40-0ubuntu0~quantal5.2) but 2.4.40-0ubuntu0~quantal5.1 is to be installed.
 libdrm-radeon1:i386 : Breaks: libdrm-radeon1 (!= 2.4.40-0ubuntu0~quantal5.1) but 2.4.40-0ubuntu0~quantal5.2 is installed.
 libcairo2 : Breaks: libcairo2:i386 (!= 1.12.4-0ubuntu0~quantal15.2) but 1.12.4-0ubuntu0~quantal15.1 is to be installed.
 libcairo2:i386 : Breaks: libcairo2 (!= 1.12.4-0ubuntu0~quantal15.1) but 1.12.4-0ubuntu0~quantal15.2 is installed.
 libdrm2 : Breaks: libdrm2:i386 (!= 2.4.40-0ubuntu0~quantal5.2) but 2.4.40-0ubuntu0~quantal5.1 is to be installed.
 libdrm2:i386 : Breaks: libdrm2 (!= 2.4.40-0ubuntu0~quantal5.1) but 2.4.40-0ubuntu0~quantal5.2 is installed.
 libdrm-intel1 : Breaks: libdrm-intel1:i386 (!= 2.4.40-0ubuntu0~quantal5.2) but 2.4.40-0ubuntu0~quantal5.1 is to be installed.
 libdrm-intel1:i386 : Breaks: libdrm-intel1 (!= 2.4.40-0ubuntu0~quantal5.1) but 2.4.40-0ubuntu0~quantal5.2 is installed.
The following actions will resolve these dependencies:

      Keep the following packages at their current version:          
1)      gstreamer0.10-plugins-good:i386 [Not Installed]              
2)      gstreamer0.10-x:i386 [Not Installed]                         
3)      gtk2-engines:i386 [Not Installed]                            
4)      gtk2-engines-murrine:i386 [Not Installed]                    
5)      gtk2-engines-oxygen:i386 [Not Installed]                     
6)      gtk2-engines-pixbuf:i386 [Not Installed]                     
7)      ia32-libs-multiarch:i386 [Not Installed]                     
8)      ibus-gtk:i386 [Not Installed]                                
9)      libcairo-gobject2:i386 [Not Installed]                       
10)     libcairo2:i386 [Not Installed]                               
11)     libcanberra-gtk-module:i386 [Not Installed]                  
12)     libcanberra-gtk0:i386 [Not Installed]                        
13)     libdrm-intel1:i386 [Not Installed]                           
14)     libdrm-nouveau2:i386 [Not Installed]                         
15)     libdrm-radeon1:i386 [Not Installed]                          
16)     libdrm2:i386 [Not Installed]                                 
17)     libgail-common:i386 [Not Installed]                          
18)     libgail18:i386 [Not Installed]                               
19)     libgl1-mesa-dri:i386 [Not Installed]                         
20)     libgl1-mesa-glx:i386 [Not Installed]                         
21)     libglu1-mesa:i386 [Not Installed]                            
22)     libgtk2.0-0:i386 [Not Installed]                             
23)     libpango1.0-0:i386 [Not Installed]                           
24)     libqt4-opengl:i386 [Not Installed]                           
25)     librsvg2-2:i386 [Not Installed]                              
26)     librsvg2-common:i386 [Not Installed]                         
27)     libvisual-0.4-plugins:i386 [Not Installed]                   

      Leave the following dependencies unresolved:                   
28)     libcanberra-gtk0:i386 recommends libcanberra-gtk-module:i386 
29)     libvisual-0.4-0:i386 recommends libvisual-0.4-plugins:i386   
30)     ia32-libs-multiarch:i386 recommends libgl1-mesa-glx:i386     
31)     ia32-libs-multiarch:i386 recommends libgl1-mesa-dri:i386     
32)     libgl1-mesa-glx:i386 recommends libgl1-mesa-dri:i386 (>= 7.2)


Accept this solution? [Y/n/q/?] Y
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.

```

---

### Post by Perfect Storm on 2013-03-15
Looks like you have some PPA's in your sourcelist that are interfering. Try disable those PPA's first.

---

### Post by mellery on 2013-03-15
How do I find what ppa's interfere?

---

### Post by Perfect Storm on 2013-03-15
Under 'software source' in Ubuntu Software Center.

---

### Post by mellery on 2013-03-15
I don't see any errors about interfering PPAs, what should I do?

---

### Post by Perfect Storm on 2013-03-15
Have you installed something that is not from the official repositories? 

You could also try installing synaptic and see if its 'fix broken packages' options can solve it.

---

### Post by duncanmacp on 2013-08-29
This is an error on steam's end. [https://github.com/ValveSoftware/steam-for-linux/issues/2800](https://github.com/ValveSoftware/steam-for-linux/issues/2800) It has to do with the Kernel upgrade. I am using a fresh install of 12.04.3 64 bit. I get the same exact results. If you could go back to the kernel you were using, it would solve your issue. I am just going to wait foe steam to solve the issue. It shouldn't take very long.... I hope.

---

### Post by duncanmacp on 2013-08-29
Okay, I found a solution!!!

Open your terminal ctr alt t

run the command

sudo apt-get install ia32-libs

sudo apt-get update

Works like a charm!

---

### Post by duncanmacp on 2013-08-29
[QUOTE=duncanmacp;12773542]Okay, I found a solution!!!

Open your terminal ctr alt t

run the command

sudo apt-get install ia32-libs

sudo apt-get update

Works like a charm![/QUOTE

Actually, it is one of the first threads that says this... Sorry, I am not the one responsible for the fix. Didn't mean to take credit...

---

