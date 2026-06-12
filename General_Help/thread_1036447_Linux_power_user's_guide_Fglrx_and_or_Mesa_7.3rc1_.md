---
title: "Linux power user's guide: Fglrx and or Mesa 7.3rc1 working all under a custom kernel"
date: 2009-01-10
forum: General Help
---

### Post by Neo_The_User on 2009-01-10
[B][U]***PLEASE DIGG THIS! I SPENT A LOT OF TIME WRITING THIS AND I WANT THIS TO BE KNOWN!***
PLEASE DO 6NTU6 BEFORE 5NTU5! SORRY FOR THE MISTAKE!
[/U][/B]

Hello! This is an advanced guide for Linux power users who want the most out of their system on Ubuntu 8.10 (specifically the graphics processor) by getting fglrx (ATi driver) and or Mesa 7.3 release candidate 1 (Beta release) working on a custom kernel (I used upstream official linux kernel 2.6.28 stable with no snapshots or Andrew Norton's patches.)

PLEASE NOTE: THIS IS NOT FOR USERS WHO SIMPLY WANT FGLRX WORKING WITH UBUNTU 8.10! IF YOU ARE TRYING TO BUILD A KERNEL AND WANT TO RESULT IN DIRECT RENDERING WITH THE LATEST VERSION OF CATALYST BUILT FOR UBUNTU 8.10 AND ARE WILLING TO DO LOTS OF COMPILING, YOU'VE CAME TO THE RIGHT PLACE! THIS GUIDE WILL BE UPDATED ONCE A MONTH TO KEEP YOU UP TO DATE WITH THE LATEST ATI DRIVERS!

**1NTU1 PREPARING YOUR SYSTEM**

If you know the basics to compile a kernel from source then go to section 2NTU2

What **I** did:

```

mkdir src && cd src
wget http://kernel.org/pub/linux/kernel/v2.6/linux-2.6.28.tar.bz2
sudo apt-get install build-essential xorg-dev fakeroot kernel-package bison makedumpfile qt3-dev-tools qt4-dev-tools git-core
tar xvjf linux-2.6.28.tar.bz2
cd linux-2.6.28
make xconfig

```

**2NTU2 Critical things you need compiled as modules or into the kernel**

Configure it your way except under Graphics support, have /dev/agpgart (AGP Support) compiled INTO the kernel (Y) and your chipset (not graphics card) compiled INTO the kernel (Y)

Right under that is the DRM (Direct Rendering Manager) and you want to compile that AS A MODULE (M) and your graphics card (not chipset) compiled as a MODULE (M) as well.

Save your config file.

Now where was I.... right. If you know how to install kernels then skip to 4NTU4 or if you need help on rebooting your computer (hehehe) go to 3NTU3

```

make-kpkg clean
fakeroot make-kpkg --initrd --append-to-version=-direct kernel-image kernel-headers
cd ..
ls

```

Type in: 
sudo dpkg -i (your kernel image)
sudo dpkg -i (your kernel headers)

**3NTU3 Restarting your computer**
Restart your computer. If you want to do it the cool way...

```

sudo telinit 6

```

Now your inside your new kernel. Typing uname -r into the terminal should answer your question if you want to be sure.

**4NTU4 Getting the source for the Xorg components**

DO ALL THIS IN THE ROOT OF YOUR HOME DIRECTORY

i.e: neo@neo-desktop:~$

```

git clone git://anongit.freedesktop.org/git/xorg/proto/glproto
git clone git://anongit.freedesktop.org/git/xorg/proto/xf86vidmodeproto
git clone git://anongit.freedesktop.org/git/xorg/lib/libXxf86vm
git clone git://anongit.freedesktop.org/git/xorg/lib/libXmu
git clone git://git.freedesktop.org/git/xorg/proto/dri2proto

```

**5NTU5 BUILDING THE XORG COMPONETS**

DO 6NTU6 BEFORE DOING THIS!

glproto
```

cd glproto
./autogen.sh
./configure --prefix=/usr
sudo make install

```

xf86vidmodeproto
```

cd ../xf86vidmodeproto
./autogen.sh
./configure --prefix=/usr
sudo make install

```

libXxf86vm
```

cd ../libXxf86vm
./autogen.sh
./configure --prefix=/usr
sudo make install

```

libXmu
```

cd ../libXmu
./autogen.sh
./configure --prefix=/usr
sudo make install

```

dri2proto
```

cd ../dri2proto
./autogen.sh
./configure --prefix=/usr
sudo make install

```

**6NTU6 GETTING DEVELOPMENT TOOLS NEEDED**

```

sudo apt-get build-dep libdrm mesa
sudo apt-get install linux-headers-`uname -r` libxi-dev libxmu-dev x11proto-xf86vidmode-dev autoconf automake libtool

```

**7NTU7 GETTING COMPILING AND BUILDING libdrm FROM SOURCE**

DO THIS AFTER YOU HAVE LEFT THE DRI2PROTO FOLDER (THE ROOT OF YOUR HOME DIRECTORY IS WHERE THIS SHOULD BE DONE)

```

git clone git://anongit.freedesktop.org/git/mesa/drm
cd drm
./autogen.sh
./configure --prefix=/usr
sudo make install

```

**8NTU8 GETTING COMPILING AND BUILDING Mesa FROM SOURCE**

Now before you do this, get out of the drm folder by doing this.

```

cd ..

```

On to the compiling and installing of Mesa

```

git clone git://anongit.freedesktop.org/mesa/mesa
cd mesa

```

If you use the i386 version of Ubuntu 8.10 and have an x86 compatible processor, you would do this.

```

make linux-dri-x86

```

HOWEVER, If you use an AMD64 processor and Ubuntu 8.10 AMD64, you would do this.

```

make linux-dri-x86-64

```

If you use neither, inside your home directory, go into the Mesa folder and go into the configs folder and type in make (whatever)

Blah blah blah. OK Now... if you have the i386 version of Ubuntu 8.10:

```

sudo cp lib/*_dri.so /usr/lib/dri/

```

For AMD64...

```

sudo cp lib64/*_dri.so /usr/X11R6/lib/modules/dri/

```

**IF YOU HAVE AN _ATI RADEON 9250_ OR OLDER JUST STOP RIGHT NOW, RESTART AND ENJOY MESA 7.3**

OK Now go back to the drm folder in your home directory. Typing this should take you straight to it.

```

cd ../drm/linux-core

```

If you still aren't back in the folder called drm, get a compass.

```

make
sudo mkdir -p /lib/modules/$KERNEL/kernel/drivers/char/drm
sudo cp *.ko /lib/modules/$KERNEL/kernel/drivers/char/drm
sudo depmod -a $KERNEL

```

**9NTU9 CONFIGURING YOUR XORG.CONF FILE BY HAND! DANGEROUS!! :confused:**

Before I edited it: [http://pastebin.ca/1305571](http://pastebin.ca/1305571) (example)

After I edited it: [http://pastebin.ca/1305572](http://pastebin.ca/1305572) (example)

Look at the end of both the files. The most important part is the Section "Module" and Section "DRI" Be absolutely sure that what I have in Section Module and Section DRI is **EXACTLY** the same in your file. Everything else you can just leave alone. Just make sure of the Section "DRI" and Section "Module" and you'll be fine.

**10NTU10 editing /etc/modprobe.conf**

For 2.6.XX kernels:

```

sudo gedit /etc/modprobe.conf

```

It should be a blank file. Now what you want to do is make it look like this. DO NOT COPY AND PASTE! REPEAT! DO NOT!

```

pre-install <radeon> /sbin/modprobe "-k" "agpgart"
pre-install agpgart /sbin/modprobe "-k" "via_agp"

```

The first line in the code box is MY graphics card (most likely yours too if you are reading this and planning to use fglrx)

The second line is my chipset. Refer to your custom kernel config and lspci output and make the etc/modprobe.conf file correct to your hardware and kernel. If you selected a different chipset in your kernel that is different than your actual chipset (lspci can tell you) then you need to recompile the kernel. Make sure you have the second line right. via_agp, intel_agp, sis_agp etc.

**11NTU11 Installing ATi drivers**

From the root of your home directory... (bring out that compass if you need to)

```

wget https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8-12-x86.x86_64.run

sudo apt-get install dh-make debconf debhelper cdbs dkms module-assistant

sudo gedit /etc/default/linux-restricted-modules-common

```

In the /etc/default/linux-restricted-modules-common file, all the way at the bottom, type in fglrx in between the quotes.

```

sh ati-driver-installer-8-12-x86.x86_64.run --buildpkg Ubuntu/intrepid

sudo dpkg -i xorg-driver-fglrx_8.561-0ubuntu1_i386.deb xorg-driver-fglrx-dev_8.561-0ubuntu1_i386.deb fglrx-kernel-source_8.561-0ubuntu1_i386.deb fglrx-amdcccle_8.561-0ubuntu1_i386.deb fglrx-modaliases_8.561-0ubuntu1_i386.deb libamdxvba1_8.561-0ubuntu1_i386.deb

```

MAKE SURE YOU INSTALL OF THEM!

```

sudo aticonfig --initial -f

```

If you have an AMD64 processor and unpacking the .deb files fails, try this.

```

sudo apt-get install -f

sudo dpkg -i --force-overwrite xorg-driver-fglrx_8.561-0ubuntu1_i386.deb xorg-driver-fglrx-dev_8.561-0ubuntu1_i386.deb fglrx-kernel-source_8.561-0ubuntu1_i386.deb fglrx-amdcccle_8.561-0ubuntu1_i386.deb fglrx-modaliases_8.561-0ubuntu1_i386.deb libamdxvba1_8.561-0ubuntu1_i386.deb

```

Now restart your computer.

```

sudo telinit 6

```

If you need to access Catalyst, go to Applications > Accessories > ATi Catalyst Control Center (it should be all the way on top)

For those who think this doesn't work, look at this.

```

neo@neo-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 PRO
OpenGL version string: 2.1.8304 Release

neo@neo-desktop:~$ uname -r
2.6.28-k7
neo@neo-desktop:~$ glxinfo | grep OpenGL
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 PRO
OpenGL version string: 2.1.8304 Release
OpenGL shading language version string: 1.20
OpenGL extensions:
neo@neo-desktop:~$ glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: RADEON 9800 PRO

```

That was copy and pasted.

One more thing, you can always go back to the 2.6.27-11-generic kernel and still have all the great benefits of Catalyst and Direct Rendering via DKMS without re-installing the ATi drivers by hand. (DKMS loads on boot if installed)

Best Regards to all!

Special thanks to my friend Rosie.

-Neo_The_User Playstation 3 developer.

:KS :o :)

---

