---
title: "Skype install on Lubuntu 14.10"
date: 2014-10-24
forum: Desktop Environments
---

### Post by ryuragnas on 2014-10-24
Hi all,

I have just installed Lubuntu 14.10 on my laptop. I have updated, upgraded, and dist-upgraded, and I am having trouble installing Skype on my laptop. I've tried using the Canonical Partners repository and I've tried installing from deb file. Installing from Canonical Partners gives me the following:

```
user@computer:~$ sudo apt-get install skype 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 skype : Depends: skype-bin
E: Unable to correct problems, you have held broken packages.
user@computer:~$ sudo apt-get install skype skype-bin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 im-config : Depends: zenity or
                      kde-baseapps-bin but it is not going to be installed or
                      dialog but it is not going to be installed
             Recommends: dialog but it is not going to be installed
 libgtk2.0-0 : Depends: libcairo2 (>= 1.6.4-6.1) but it is not going to be installed
               Depends: libgdk-pixbuf2.0-0 (>= 2.22.0) but it is not going to be installed
               Depends: libpangocairo-1.0-0 (>= 1.28.3) but it is not going to be installed
               Depends: libpangoft2-1.0-0 (>= 1.28.3) but it is not going to be installed
               Recommends: libgtk2.0-bin
 libpng12-0 : Breaks: libpng12-0:i386 (!= 1.2.51-0ubuntu3) but 1.2.51-0ubuntu2 is to be installed
 libpng12-0:i386 : Breaks: libpng12-0 (!= 1.2.51-0ubuntu2) but 1.2.51-0ubuntu3 is to be installed
 libqapt2-runtime : Depends: libpolkit-qt-1-1 (>= 0.99.0) but it is not going to be installed
                    Depends: polkit-kde-1 but it is not going to be installed or
                             policykit-1-gnome
 libqt5gui5 : Depends: libxkbcommon-x11-0 (>= 0.4.0) but it is not going to be installed
 skype-bin:i386 : Depends: libqt4-dbus:i386 (>= 4:4.5.3) but it is not going to be installed
                  Depends: libqt4-network:i386 (>= 4:4.8.0) but it is not going to be installed
                  Depends: libqt4-xml:i386 (>= 4:4.5.3) but it is not going to be installed
                  Depends: libqtcore4:i386 (>= 4:4.7.0~beta1) but it is not going to be installed
                  Depends: libqtgui4:i386 (>= 4:4.8.0) but it is not going to be installed
                  Depends: libqtwebkit4:i386 (>= 2.2~2011week36) but it is not going to be installed
                  Depends: libssl1.0.0:i386 but it is not going to be installed
                  Depends: libgl1-mesa-glx:i386 but it is not going to be installed
                  Recommends: sni-qt:i386 but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

```

If I install from deb file using gdebi, it says:

```
user@computer:~/Downloads$ sudo dpkg -i skype-ubuntu-precise_4.3.0.37-1_i386.deb 
Selecting previously unselected package skype.
(Reading database ... 125339 files and directories currently installed.)
Preparing to unpack skype-ubuntu-precise_4.3.0.37-1_i386.deb ...
Unpacking skype (4.3.0.37-1) ...
dpkg: dependency problems prevent configuration of skype:
 skype depends on libc6 (>= 2.3.6-6~).
 skype depends on libc6 (>= 2.7).
 skype depends on libgcc1 (>= 1:4.1.1).
 skype depends on libqt4-dbus (>= 4:4.5.3).
 skype depends on libqt4-network (>= 4:4.8.0).
 skype depends on libqt4-xml (>= 4:4.5.3).
 skype depends on libqtcore4 (>= 4:4.7.0~beta1).
 skype depends on libqtgui4 (>= 4:4.8.0).
 skype depends on libqtwebkit4 (>= 2.2~2011week36).
 skype depends on libstdc++6 (>= 4.2.1).
 skype depends on libx11-6.
 skype depends on libxext6.
 skype depends on libxss1.
 skype depends on libxv1.
 skype depends on libssl1.0.0.
 skype depends on libpulse0.
 skype depends on libasound2-plugins.

dpkg: error processing package skype (--install):
 dependency problems - leaving unconfigured
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu2) ...
Processing triggers for mime-support (3.55ubuntu1) ...
Processing triggers for dbus (1.8.8-1ubuntu2) ...
Errors were encountered while processing:
 skype

user@computer:~/Downloads$ sudo apt-get -f install 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  ca-certificates-java fonts-dejavu-extra gcc-4.9-base:i386 libasound2:i386
  libasound2-plugins:i386 libasyncns0:i386 libatk-wrapper-java
  libatk-wrapper-java-jni libavahi-client3:i386 libavahi-common-data:i386
  libavahi-common3:i386 libbasicusageenvironment0 libbonobo2-0
  libbonobo2-common libc6:i386 libcdparanoia0:i386 libcomerr2:i386
  libcrystalhd3 libdbus-1-3:i386 libdrm-nouveau2:i386 libdrm-radeon1:i386
  libdrm2:i386 libdvbpsi9 libebml4 libedit2:i386 libelf1:i386 libffi6:i386
  libfftw3-single3 libflac8:i386 libgcc1:i386 libgconf2-4 libgcrypt11:i386
  libglapi-mesa:i386 libgles1-mesa libglew1.10 libgnome2-0 libgnome2-bin
  libgnome2-common libgnomevfs2-0 libgnomevfs2-common libgpg-error0:i386
  libgroupsock1 libice6:i386 libiso9660-8 libjack-jackd2-0:i386 libjbig0:i386
  libjpeg-turbo8:i386 libjpeg8:i386 libjson-c2:i386 libk5crypto3:i386
  libkrb5support0:i386 liblcms1 liblivemedia23 libllvm3.5:i386 liblqr-1-0
  liblzma5:i386 libmatroska6 libmozjs185-1.0 libmysqlclient18
  libmysqlclient18:i386 libnettle4:i386 libogg0:i386 liborbit-2-0
  liborc-0.4-0:i386 libp11-kit0:i386 libpcre3:i386 libproxy-tools
  libpulse0:i386 libqt4-network libqt4-script libqt4-sql libqt4-sql-mysql
  libqt4-xml libqt4-xmlpatterns libqtcore4 libqtdbus4 libresid-builder0c2a
  libsamplerate0:i386 libshine3 libsidplay2 libsndfile1:i386 libspeexdsp1:i386
  libsqlite3-0:i386 libstdc++6:i386 libtasn1-6:i386 libtheora0:i386
  libtiff-tools libtinfo5:i386 libtxc-dxtn-s2tc0:i386 libupnp6
  libusageenvironment1 libva-drm1 libva-glx1 libva-x11-1 libvcdinfo0
  libvisual-0.4-0:i386 libvlc5 libvlccore8 libvorbis0a:i386 libvorbisenc2:i386
  libwrap0:i386 libx11-6:i386 libx11-xcb1:i386 libxau6:i386 libxcb-composite0
  libxcb-dri2-0:i386 libxcb-dri3-0:i386 libxcb-glx0:i386 libxcb-keysyms1
  libxcb-present0:i386 libxcb-sync1:i386 libxcb-xv0 libxcb1:i386
  libxdamage1:i386 libxdmcp6:i386 libxext6:i386 libxfixes3:i386 libxi6:i386
  libxine2-bin libxine2-doc libxine2-ffmpeg libxine2-gnome libxine2-x
  libxrender1:i386 libxshmfence1:i386 libxss1:i386 libxv1:i386
  libxxf86vm1:i386 mysql-common openjdk-7-jre-headless qdbus qtchooser
  qtcore4-l10n tzdata-java vlc-data x11-session-utils xinit zlib1g:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gcc-4.9-base:i386 libasound2:i386 libasound2-plugins:i386 libasyncns0:i386
  libc6:i386 libdbus-1-3:i386 libflac8:i386 libgcc1:i386 libjack-jackd2-0:i386
  libjson-c2:i386 libogg0:i386 libpulse0:i386 libsamplerate0:i386
  libsndfile1:i386 libspeexdsp1:i386 libstdc++6:i386 libvorbis0a:i386
  libvorbisenc2:i386 libwrap0:i386 libx11-6:i386 libxau6:i386 libxcb1:i386
  libxdmcp6:i386 libxext6:i386 libxss1:i386 libxv1:i386
Suggested packages:
  glibc-doc:i386 locales:i386 jackd2:i386 pulseaudio:i386
The following packages will be REMOVED:
  abiword easytag evince gimp gimp-gmic gimp-plugin-registry
  google-chrome-stable gstreamer0.10-plugins-bad gstreamer1.0-plugins-bad
  guvcview gxine libabiword-3.0 libcurl3 libebook-contacts-1.2-0
  libedataserver-1.2-18 libevdocument3-4 libevview3-3 libfreerdp1
  libgegl-0.2-0 libgraphicsmagick3 libopusfile0 libpoppler-glib8
  libqt4-declarative libqtgui4 libsdl-image1.2 libvncclient0
  libwebkitgtk-1.0-0 libwv-1.2-4 libxine2 libxine2-misc-plugins
  libxine2-plugins libzvbi0 lubuntu-core lubuntu-desktop lxappearance-obconf
  mtpaint openjdk-7-jre python-crypto python-secretstorage skype:i386 vlc
  vlc-nox vlc-plugin-notify vlc-plugin-samba whoopsie x11-apps xorg
The following NEW packages will be installed:
  gcc-4.9-base:i386 libasound2:i386 libasound2-plugins:i386 libasyncns0:i386
  libc6:i386 libdbus-1-3:i386 libflac8:i386 libgcc1:i386 libjack-jackd2-0:i386
  libjson-c2:i386 libogg0:i386 libpulse0:i386 libsamplerate0:i386
  libsndfile1:i386 libspeexdsp1:i386 libstdc++6:i386 libvorbis0a:i386
  libvorbisenc2:i386 libwrap0:i386 libx11-6:i386 libxau6:i386 libxcb1:i386
  libxdmcp6:i386 libxext6:i386 libxss1:i386 libxv1:i386
0 to upgrade, 26 to newly install, 47 to remove and 0 not to upgrade.
1 not fully installed or removed.
Need to get 7,492 kB of archives.
After this operation, 354 MB disk space will be freed.
Do you want to continue? [Y/n] 

```

I am afraid if I answer yes, that it will remove too much of my install, and I will have to reinstall. Anyway I can get Skype installed on Lubuntu 14.10?

---

