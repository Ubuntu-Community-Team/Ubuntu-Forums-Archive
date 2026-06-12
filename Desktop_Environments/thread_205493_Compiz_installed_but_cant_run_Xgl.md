---
title: "Compiz installed but cant run Xgl"
date: 2006-06-28
forum: Desktop Environments
---

### Post by Hg80 on 2006-06-28
right compiz is installed i can find it and view it,but when i try to check it using the terminal i get this 
```
hg@hg80:~$ /usr/bin/compiz /usr/bin/compiz: error while loading shared libraries: libXcomposite.so.1: cannot open shared object file: No such file or directory hg@hg80:~$ 
```

ok so i try to install the package using
```
 sudo apt-get install libx11-6 libx11-dev libxau-dev libxau6 libxcompo site-dev libxcomposite1 libxcursor-dev libxcursor1 libxdamage-dev libxdamage1 li bxdmcp-dev libxdmcp6 libxext-dev libxext6 libxfixes-dev libxfixes3 libxfont-dev libxfont1 libxft-dev libxft2 libxi-dev libxi6 libxinerama-dev libxinerama1 libxk bfile-dev libxkbfile1 libxklavier10 libxmu-dev libxmu-headers libxmu6 libxmuu-de v libxmuu1 libxp6 libxpm-dev libxpm4 libxrandr-dev libxrandr2 libxrender-dev lib xrender1 libxres1 libxss1 libxt-dev libxt6 libxtrap-dev libxtrap6 libxtst-dev li bxtst6 libxv-dev libxv1 libxvmc1 libxxf86dga1 libxxf86misc1 libxxf86vm1 x11proto -bigreqs-dev x11proto-composite-dev x11proto-core-dev x11proto-damage-dev x11pro to-fixes-dev x11proto-fonts-dev x11proto-input-dev x11proto-kb-dev x11proto-rand r-dev x11proto-record-dev x11proto-render-dev x11proto-resource-dev x11proto-scr nsaver-dev x11proto-randr-dev x11proto-record-dev x11proto-render-dev x11proto-r esource-dev x11proto-scrnsaver-dev x11proto-trap-dev x11proto-video-dev x11proto -xcmisc-dev x11proto-xext-dev x11proto-xinerama-dev libpng12-dev build-essential  gcc gcc-3.4 libncurses5 libncurses5-dev libqt3-mt-dev m4 autoconf automake1.7 a utotools-dev libtool libxfont-dev xtrans-dev libfreetype6-dev zlib1g-dev libgl1- mesa-dev gconf libgconf-dev gconf-editor cvs libgconf2-dev libwnck-dev

```

but get this
```
Reading package lists... Done
Building dependency tree... Done
libx11-6 is already the newest version.
libxau6 is already the newest version.
libxcursor1 is already the newest version.
libxdamage1 is already the newest version.
libxdmcp6 is already the newest version.
libxext6 is already the newest version.
libxfixes3 is already the newest version.
libxfont1 is already the newest version.
libxft2 is already the newest version.
libxi6 is already the newest version.
libxinerama1 is already the newest version.
libxkbfile1 is already the newest version.
libxklavier10 is already the newest version.
libxmu6 is already the newest version.
libxmuu1 is already the newest version.
libxp6 is already the newest version.
libxpm4 is already the newest version.
libxrandr2 is already the newest version.
libxrender1 is already the newest version.
libxres1 is already the newest version.
libxss1 is already the newest version.
libxt6 is already the newest version.
libxtrap6 is already the newest version.
libxtst6 is already the newest version.
libxv1 is already the newest version.
libxvmc1 is already the newest version.
libxxf86dga1 is already the newest version.
libxxf86misc1 is already the newest version.
libxxf86vm1 is already the newest version.
libncurses5 is already the newest version.
gconf-editor is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  build-essential: Depends: libc6-dev but it is not going to be installedor
                            libc-dev
                   Depends: g++ (>= 4:4.0) but it is not going to be installed
  gcc: Depends: cpp (>= 4:4.0.1-3) but it is not going to be installed
       Depends: gcc-4.0 (>= 4.0.1-2) but it is not going to be installed
  libfreetype6-dev: Depends: libfreetype6 (= 2.1.7-2.4ubuntu1.1) but 2.1.10-1ubu ntu2.1 is to be installed
                    Depends: libc6-dev but it is not going to be installedor
                             libc-dev
  libgconf-dev: Depends: liboaf-dev but it is not going to be installed
  libgconf2-dev: Depends: libgconf2-4 (= 2.12.0-0ubuntu1) but 2.14.0-1ubuntu2 is  to be installed
                 Depends: libglib2.0-dev but it is not going to be installed
                 Depends: libpopt-dev but it is not going to be installed
                 Depends: liborbit2-dev (>= 1:2.8.0) but it is not going to be i nstalled
  libgl1-mesa-dev: Depends: libgl1-mesa (= 6.3.2-0ubuntu6breezy1) but 6.4.1-0ubu ntu8 is to be installed
                   Depends: libc6-dev but it is not going to be installed
                   Depends: x11proto-gl-dev but it is not going to be installed
  libncurses5-dev: Depends: libncurses5 (= 5.4-9ubuntu4) but 5.5-1ubuntu3 is to be installed
                   Depends: libc-dev
  libpng12-dev: Depends: libpng12-0 (= 1.2.8rel-1ubuntu3) but 1.2.8rel-5 is to b e installed
  libqt3-mt-dev: Depends: libsm-dev (>= 4.3.0.dfsg.1-4) but it is not going to b e installed
                 Depends: libice-dev (>= 4.3.0.dfsg.1-4) but it is not going to be installed
                 Depends: libmng-dev (>= 1.0.3) but it is not going to be instal led
                 Depends: libjpeg62-dev but it is not going to be installed
                 Depends: libc6-dev but it is not going to be installed
                 Depends: libglu1-mesa-dev but it is not going to be installedor
                          libglu-dev
  libtool: Depends: cpp but it is not going to be installed
           Depends: libc6-dev but it is not going to be installedor
                    libc-dev
  libwnck-dev: Depends: libwnck18 (= 2.12.1-0ubuntu2) but 2.14.2-0ubuntu1 is to be installed
               Depends: libgtk2.0-dev (>= 2.5.4) but it is not going to be insta lled
               Depends: libstartup-notification0-dev (>= 0.5) but it is not goin g to be installed
  libx11-dev: Depends: x-common but it is not going to be installed
              Depends: libx11-6 (= 1:6.2.1+cvs.20050722-8) but 2:1.0.0-0ubuntu9 is to be installed
              PreDepends: x-common (>= 1.0) but it is not going to be installed
  libxau-dev: Depends: x-common but it is not going to be installed
              Depends: libxau6 (= 1:0.1.2-2) but 1:1.0.0-0ubuntu4 is to be insta lled
              PreDepends: x-common (>= 1.0) but it is not going to be installed
  libxcomposite-dev: Depends: x-common but it is not going to be installed
                     PreDepends: x-common (>= 1.0) but it is not going to be ins talled
  libxcomposite1: Depends: x-common but it is not going to be installed
  libxcursor-dev: Depends: libxcursor1 (= 1.1.4-0ubuntu5) but 1.1.5.2-0ubuntu4 i s to be installed
                  PreDepends: x-common (>= 1.0) but it is not going to be instal led
  libxdamage-dev: Depends: x-common but it is not going to be installed
                  Depends: libxdamage1 (= 1:1.0.1-3) but 1:1.0.2.2-0ubuntu2 is t o be installed
                  PreDepends: x-common (>= 1.0) but it is not going to be instal led
  libxdmcp-dev: Depends: x-common but it is not going to be installed
                Depends: libxdmcp6 (= 1:0.1.3-2) but 1:1.0.0-0ubuntu2 is to be i nstalled
                PreDepends: x-common (>= 1.0) but it is not going to be installe d
  libxext-dev: Depends: x-common but it is not going to be installed
               Depends: libxext6 (= 1:6.4.3-3) but 2:1.0.0-0ubuntu4 is to be ins talled
               PreDepends: x-common (>= 1.0) but it is not going to be installed
  libxfixes-dev: Depends: x-common but it is not going to be installed
                 Depends: libxfixes3 (= 1:3.0.0-3) but 1:3.0.1.2-0ubuntu3 is to be installed
                 PreDepends: x-common (>= 1.0) but it is not going to be install ed
  libxfont-dev: Depends: x-common but it is not going to be installed
                Depends: libxfont1 (= 1:0.99.0+cvs.20050909-1) but 1:1.0.0-0ubun tu3 is to be installed
                PreDepends: x-common (>= 1.0) but it is not going to be installe d
  libxft-dev: Depends: libxft2 (= 2.1.7-1ubuntu5) but 2.1.8.2-0ubuntu2 is to be installed
              Depends: libc6-dev but it is not going to be installedor
                       libc-dev
              Depends: libfontconfig1-dev but it is not going to be installed
              PreDepends: x-common (>= 1.0) but it is not going to be installed
  libxi-dev: Depends: x-common but it is not going to be installed
             Depends: libxi6 (= 1:1.3.0-2) but 2:1.0.0-0ubuntu3 is to be install ed
             PreDepends: x-common (>= 1.0) but it is not going to be installed
  libxinerama-dev: Depends: x-common but it is not going to be installed
                   Depends: libxinerama1 (= 1:1.1.0+cvs.20050821-1) but 2:1.0.1- 0ubuntu2 is to be installed
                   PreDepends: x-common (>= 1.0) but it is not going to be insta lled
  libxkbfile-dev: Depends: x-common but it is not going to be installed
                  Depends: libxkbfile1 (= 7.0.0-3) but 1:1.0.1-0ubuntu2 is to be  installed
                  PreDepends: x-common (>= 1.0) but it is not going to be instal led
  libxmu-dev: Depends: x-common but it is not going to be installed
              Depends: libxmu6 (= 1:6.2.3-5) but 2:1.0.0-0ubuntu3 is to be insta lled
  libxmu-headers: PreDepends: x-common (>= 1.0) but it is not going to be instal led
  libxmuu-dev: Depends: x-common but it is not going to be installed
               Depends: libxmuu1 (= 1:6.2.3-5) but 2:1.0.0-0ubuntu3 is to be ins talled
  libxpm-dev: Depends: x-common but it is not going to be installed
              Depends: libxpm4 (= 1:3.5.2-5) but 1:3.5.4.2-0ubuntu3 is to be ins talled
              PreDepends: x-common (>= 1.0) but it is not going to be installed
  libxrandr-dev: Depends: x-common but it is not going to be installed
                 Depends: libxrandr2 (= 1:1.0.2-2) but 1:1.1.0.2-0ubuntu4 is to be installed
                 PreDepends: x-common (>= 1.0) but it is not going to be install ed
  libxrender-dev: Depends: libxrender1 (= 1:0.9.0-1) but 1:0.9.0.2-0ubuntu2 is t o be installed
                  PreDepends: x-common (>= 1.0) but it is not going to be instal led
  libxt-dev: Depends: x-common but it is not going to be installed
             Depends: libxt6 (= 1:0.99.0+cvs.20050803-3) but 1:1.0.0-0ubuntu3 is  to be installed
             Depends: libsm-dev but it is not going to be installed
             PreDepends: x-common (>= 1.0) but it is not going to be installed
  libxtrap-dev: Depends: x-common but it is not going to be installed
                Depends: libxtrap6 (= 1:3.0.0-3) but 2:1.0.0-0ubuntu2 is to be i nstalled
                PreDepends: x-common (>= 1.0) but it is not going to be installe d
  libxtst-dev: Depends: x-common but it is not going to be installed
               Depends: libxtst6 (= 1:1.13.0-2) but 2:1.0.1-0ubuntu2 is to be in stalled
               PreDepends: x-common (>= 1.0) but it is not going to be installed
  libxv-dev: Depends: x-common but it is not going to be installed
             Depends: libxv1 (= 1:2.2.0+cvs.20050712-3) but 2:1.0.1-0ubuntu3 is to be installed
             PreDepends: x-common (>= 1.0) but it is not going to be installed
  x11proto-bigreqs-dev: Depends: x-common but it is not going to be installed
                        PreDepends: x-common (>= 1.0) but it is not going to be installed
  x11proto-composite-dev: Depends: x-common but it is not going to be installed
                          PreDepends: x-common (>= 1.0) but it is not going to b e installed
  x11proto-core-dev: Depends: x-common but it is not going to be installed
                     PreDepends: x-common (>= 0.99) but it is not going to be in stalled
  x11proto-damage-dev: Depends: x-common but it is not going to be installed
                       PreDepends: x-common (>= 1.0) but it is not going to be i nstalled
  x11proto-fixes-dev: Depends: x-common but it is not going to be installed
                      PreDepends: x-common (>= 1.0) but it is not going to be in stalled
  x11proto-fonts-dev: Depends: x-common but it is not going to be installed
                      PreDepends: x-common (>= 1.0) but it is not going to be in stalled
  x11proto-input-dev: Depends: x-common but it is not going to be installed
                      PreDepends: x-common (>= 1.0) but it is not going to be in stalled
  x11proto-kb-dev: Depends: x-common but it is not going to be installed
                   PreDepends: x-common (>= 1.0) but it is not going to be insta lled
  x11proto-randr-dev: Depends: x-common but it is not going to be installed
                      PreDepends: x-common (>= 1.0) but it is not going to be in stalled
  x11proto-record-dev: Depends: x-common but it is not going to be installed
                       PreDepends: x-common (>= 1.0) but it is not going to be i nstalled
  x11proto-render-dev: Depends: x-common but it is not going to be installed
                       PreDepends: x-common (>= 1.0) but it is not going to be i nstalled
  x11proto-resource-dev: Depends: x-common but it is not going to be installed
                         PreDepends: x-common (>= 1.0) but it is not going to be  installed
  x11proto-scrnsaver-dev: Depends: x-common but it is not going to be installed
                          PreDepends: x-common (>= 1.0) but it is not going to b e installed
  x11proto-trap-dev: Depends: x-common but it is not going to be installed
                     PreDepends: x-common (>= 1.0) but it is not going to be ins talled
  x11proto-video-dev: Depends: x-common but it is not going to be installed
                      PreDepends: x-common (>= 1.0) but it is not going to be in stalled
  x11proto-xcmisc-dev: Depends: x-common but it is not going to be installed
                       PreDepends: x-common (>= 1.0) but it is not going to be i nstalled
  x11proto-xext-dev: Depends: x-common but it is not going to be installed
                     PreDepends: x-common (>= 1.0) but it is not going to be ins talled
  x11proto-xinerama-dev: Depends: x-common but it is not going to be installed
                         PreDepends: x-common (>= 1.0) but it is not going to be  installed
  xtrans-dev: PreDepends: x-common (>= 0.99) but it is not going to be installed
  zlib1g-dev: Depends: zlib1g (= 1:1.2.3-3ubuntu4) but 1:1.2.3-6ubuntu4 is to be  installed
              Depends: libc6-dev but it is not going to be installedor
                       libc-dev

```

And now im stuck, i am running 64bit 6.06, help please

---

