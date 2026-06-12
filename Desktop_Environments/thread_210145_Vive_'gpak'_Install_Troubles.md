---
title: "Vive 'gpak' Install Troubles"
date: 2006-07-06
forum: Desktop Environments
---

### Post by dpaint4 on 2006-07-06
I'm trying to follow the install guide for Vive ([http://vive.sourceforge.net/install.php](http://vive.sourceforge.net/install.php)) but I've run into countless troubles during the process. 

The latest is that durring my installation of gpac and gpak_extra_libs I get an error in Terminal stating that zlib is not found.

Actually 'zlib' specifically is not on my system, but I have the Ubuntu version, 'zlib1g'. 'zlib' is not available to me through the package manager.

The maker of Vive is an Ubuntu user (on these forums no less), so this whole issue puzzles me. I'm eager to get on with the install. I remember this working flawlessly when I used 5.10, but 6.06 seems to like the whole install process a good deal less.

This is the code where my woes began:

> Please install MP4Box by running:
        ./install mp4box
Or, run the following commands by yourself:
        wget [http://internap.dl.sourceforge.net/sourceforge/gpac/gpac-0.4.0-rc2](http://internap.dl.sourceforge.net/sourceforge/gpac/gpac-0.4.0-rc2). tar.gz
        wget [http://internap.dl.sourceforge.net/sourceforge/gpac/gpac_extra_libs](http://internap.dl.sourceforge.net/sourceforge/gpac/gpac_extra_libs) -0.4.0.tar.gz
        tar -zxf gpac-0.4.0-rc2.tar.gz
        tar -zxf  gpac_extra_libs-0.4.0.tar.gz
        cd gpac_extra_libs
        cp -r * ../gpac/extra_lib
        cd ../gpac
        chmod +x configure
        ./configure
        make lib
        make apps
        make install
        sudo cp bin/gcc/libgpac.so /usr/lib


I tried ./install mp4box, but only got a 'no such file or directory'.

So then I tried doing the manual install like it states as the alternative. The downloads went fine but during the ./configure, I hit the thing about the missing zlib.

---

