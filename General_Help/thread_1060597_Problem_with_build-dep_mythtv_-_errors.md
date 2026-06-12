---
title: "Problem with build-dep mythtv - errors"
date: 2009-02-04
forum: General Help
---

### Post by tiger.woods on 2009-02-04
I'm trying to install the dependancies for Mythtv and am getting the following error on 8.10. 

Can anyone tell me how to fix this?

0 upgraded, 78 newly installed, 0 to remove and 0 not upgraded.
E: Package liblame-dev has no installation candidate
E: Failed to process build dependencies

TW,

---

### Post by mc4man on 2009-02-04
liblame0 and liblame-dev aren't used in Intrepid, they've been replaced by libmp3lame0 and libmp3lame-dev.

I'd try building off of those, if no go see if there is a more recent source.

Technically you can install liblame0 and liblame-dev (from hardy) but only if libmp3lame0 and libmp3lame-dev are removed which will break some AV apps.

edit;

When you ran the build-dep it would have shown you all the packages needed (though maybe not all, but a decent start.
You can copy them to a text file, backspace each line starting at line 2 till it meets the previous and then enter a space. Use that in a apt-get install command 

something like this, then rerun the build-dep again to ck.

> 
sudo apt-get install autotools-dev build-essential ccache comerr-dev debhelper dpatch dpkg-dev g++ g++-4.3 gettext html2text intltool-debian libartsc0-dev libasound2-dev libaudio-dev libavc1394-dev libcups2-dev libcupsys2-dev libdts-dev libdvb-dev libdvdnav-dev libdvdread-dev libexpat1-dev libfaac-dev libfaac0 libfaad-dev libfftw3-dev libfontconfig1-dev libfreetype6-dev libgcrypt11-dev libgif-dev libgl1-mesa-dev libglib2.0-dev libglu1-mesa-dev libgnutls-dev libgpg-error-dev libice-dev libiec61883-dev libimlib2-dev libjack-dev libjack0.100.0-dev libjpeg62-dev libkadm55 libkrb5-dev liblcms1-dev liblircclient-dev libltdl7-dev libmail-sendmail-perl libmng-dev libmysqlclient15-dev libogg-dev libpng12-dev libpthread-stubs0 libpthread-stubs0-dev libqt3-compat-headers libqt3-headers libqt3-mt-dev libraw1394-dev libsm-dev libstdc++6-4.3-dev libsys-hostname-long-perl libtasn1-3-dev libtiff4-dev libtiffxx0c2 libtool libungif4-dev libvorbis-dev libx11-dev libx264-dev libxau-dev libxcb-xlib0-dev libxcb1-dev libxcursor-dev libxdmcp-dev libxext-dev libxfixes-dev libxft-dev libxi-dev libxinerama-dev libxmu-dev libxmu-headers libxrandr-dev libxrender-dev libxt-dev libxv-dev libxvidcore4 libxvidcore4-dev libxvmc-dev libxxf86vm-dev mesa-common-dev patchutils po-debconf qt3-dev-tools texi2html x11proto-core-dev x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev x11proto-randr-dev x11proto-render-dev x11proto-video-dev x11proto-xext-dev x11proto-xf86vidmode-dev x11proto-xinerama-dev xtrans-dev zlib1g-dev libmp3lame-dev

Or just install liblame0 and liblame-dev from hardy and do your build-dep and build

---

