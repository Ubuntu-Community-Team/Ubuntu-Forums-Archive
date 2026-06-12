---
title: "Cannot update"
date: 2014-02-19
forum: Desktop Environments
---

### Post by Bisneff on 2014-02-19
Hi,

I was lookin for use Steam. I've installed it but when I try to run it says I had to add some repository for have a best graphic.

I followed this guide [https://support.steampowered.com/kb_article.php?ref=5452-IOSM-1474](https://support.steampowered.com/kb_article.php?ref=5452-IOSM-1474) and then start updating. I give me a problem on update manager. "Not all updates can be installed" and it ask me for a partial upgrade. When I try to run it it give me this error:

```

Can't guess meta-package

Your system does not contain a ubuntu-desktop, kubuntu-desktop, xubuntu-desktop or edubuntu-desktop package and it was not possible to detect which version of Ubuntu you are running.
 Please install one of the packages above first using synaptic or apt-get before proceeding.

```

I've checked and "ubuntu-desktop" is already installed on my pc. Btw when I close the window, another one is showed:

```

Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade:
The package 'ubuntu-desktop' is marked for removal but it is in the removal blacklist.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

This is most likely a transient problem, please try again later.


```

I followed some links and I get this command:

```

bisneff@bisneff-N550JV:~$ grep Broken /var/log/dist-upgrade/apt.log
Broken libgl1-mesa-dev:amd64 Depends on libgl1-mesa-glx [ amd64 ] < none -> 9.0-0ubuntu1 > ( libs ) (= 9.0-0ubuntu1)
Broken libglu1-mesa-dev:amd64 Depends on libgl1-mesa-dev [ amd64 ] < 8.0.4-0ubuntu0.7 -> 9.0-0ubuntu1 > ( libdevel )
Broken libglu1-mesa-dev:amd64 Depends on libgl1-mesa-dev-lts-quantal [ amd64 ] < none -> 9.0.3-0ubuntu0.4~precise1 > ( libdevel )
Broken libglu1-mesa-dev:amd64 Depends on libgl1-mesa-dev-lts-raring [ amd64 ] < none -> 9.1.7-1ubuntu2~precise1 > ( libdevel )
Broken libgl1-mesa-glx-lts-raring:amd64 Depends on libglapi-mesa-lts-raring [ amd64 ] < 9.1.7-1ubuntu2~precise1 > ( libs ) (= 9.1.7-1ubuntu2~precise1)
Broken xorg:amd64 Depends on libgl1-mesa-glx [ amd64 ] < none -> 9.0-0ubuntu1 > ( libs )
Broken libgl1-mesa-dev-lts-raring:amd64 Depends on libgl1-mesa-glx-lts-raring [ amd64 ] < 9.1.7-1ubuntu2~precise1 > ( libs ) (= 9.1.7-1ubuntu2~precise1)
Broken xserver-xorg-lts-raring:amd64 Conflicts on libgl1-mesa-glx [ amd64 ] < none -> 9.0-0ubuntu1 > ( libs ) (>= 0~)
Broken ia32-libs-multiarch:i386 Depends on libglapi-mesa [ i386 ] < none -> 9.0-0ubuntu1 > ( libs )
Broken skype-bin:i386 Depends on libgl1-mesa-glx [ i386 ] < none -> 9.0-0ubuntu1 > ( libs )
Broken libgl1-mesa-dri-lts-raring:amd64 Depends on libglapi-mesa-lts-raring [ amd64 ] < 9.1.7-1ubuntu2~precise1 > ( libs )
Broken libglapi-mesa-lts-raring:amd64 Conflicts on libglapi-mesa [ amd64 ] < none -> 9.0-0ubuntu1 > ( libs )
Broken libqt4-opengl-dev:amd64 Depends on libgl1-mesa-dev [ amd64 ] < 8.0.4-0ubuntu0.7 -> 9.0-0ubuntu1 > ( libdevel )
Broken libqt4-opengl-dev:amd64 Depends on libgl-dev [ amd64 ] < none > ( none )
Broken libgl1-mesa-dev:amd64 Depends on libgl1-mesa-glx [ amd64 ] < none -> 9.0-0ubuntu1 > ( libs ) (= 8.0.4-0ubuntu0.7)
Broken libgl1-mesa-dev:amd64 Depends on libgl1-mesa-glx-lts-quantal [ amd64 ] < none -> 9.0.3-0ubuntu0.4~precise1 > ( libs )
Broken libgl1-mesa-dev:amd64 Depends on libgl1-mesa-glx-lts-raring [ amd64 ] < 9.1.7-1ubuntu2~precise1 > ( libs )
Broken libgl1-mesa-dev:amd64 Depends on libgl1-mesa-glx-lts-saucy [ amd64 ] < none -> 9.2.1-1ubuntu3~precise1 > ( libs )
Broken libvisual-0.4-plugins:i386 Depends on libgl1-mesa-glx [ i386 ] < none -> 9.0-0ubuntu1 > ( libs )
Broken libvisual-0.4-plugins:i386 Depends on libgl1 [ i386 ] < none > ( none )
Broken libglu1-mesa:i386 Depends on libgl1-mesa-glx [ i386 ] < none -> 9.0-0ubuntu1 > ( libs )
Broken freeglut3:amd64 Depends on libgl1-mesa-glx [ amd64 ] < none -> 9.0-0ubuntu1 > ( libs )
Broken libglapi-mesa-lts-raring:i386 Conflicts on libglapi-mesa [ amd64 ] < none -> 9.0-0ubuntu1 > ( libs )
Broken libglapi-mesa-lts-raring:i386 Conflicts on libglapi-mesa [ i386 ] < none -> 9.0-0ubuntu1 > ( libs )
Broken xorg:amd64 Depends on xserver-xorg [ amd64 ] < none -> 1:7.6+12ubuntu2 > ( x11 ) (>= 1:7.6+12ubuntu2)
Broken xorg:amd64 Depends on libgl1-mesa-dri [ amd64 ] < none -> 9.0-0ubuntu1 > ( libs )
Broken ubuntu-desktop:amd64 Depends on xorg [ amd64 ] < 1:7.6+12ubuntu2 > ( x11 )
Broken ia32-libs:amd64 Depends on ia32-libs-multiarch [ amd64 ] < none > ( none )
Broken xserver-xorg-video-vmware:amd64 Depends on libxatracker1 [ amd64 ] < none -> 9.0-0ubuntu1 > ( libs )
Broken ia32-libs-multiarch:i386 Depends on libglapi-mesa [ i386 ] < none -> 9.0-0ubuntu1 > ( libs )
Broken skype:amd64 Depends on skype-bin [ amd64 ] < none > ( none )
Broken libgl1-mesa-glx:amd64 Depends on libglapi-mesa [ amd64 ] < none -> 9.0-0ubuntu1 > ( libs ) (= 9.0-0ubuntu1)
Broken x11-utils:amd64 Depends on libgl1-mesa-glx [ amd64 ] < none -> 9.0-0ubuntu1 > ( libs )
Broken libgl1-mesa-glx:i386 Depends on libglapi-mesa [ i386 ] < none -> 9.0-0ubuntu1 > ( libs ) (= 9.0-0ubuntu1)
Broken libgl1-mesa-dev:amd64 Depends on mesa-common-dev [ amd64 ] < 8.0.4-0ubuntu0.7 -> 9.0-0ubuntu1 > ( devel ) (= 8.0.4-0ubuntu0.7)
Broken libgl1-mesa-dev:amd64 Depends on mesa-common-dev-lts-quantal [ amd64 ] < none -> 9.0.3-0ubuntu0.4~precise1 > ( libdevel )
Broken libgl1-mesa-dev:amd64 Depends on libgl1-mesa-glx [ amd64 ] < none -> 9.0-0ubuntu1 > ( libs ) (= 8.0.4-0ubuntu0.7)
Broken libgl1-mesa-dev:amd64 Depends on libgl1-mesa-glx-lts-quantal [ amd64 ] < none -> 9.0.3-0ubuntu0.4~precise1 > ( libs )
Broken xserver-xorg:amd64 Conflicts on xorg-renamed-package [ amd64 ] < none > ( none )
Broken libvisual-0.4-plugins:amd64 Depends on libgl1-mesa-glx [ amd64 ] < none -> 9.0-0ubuntu1 > ( libs )
Broken libglu1-mesa:i386 Depends on libgl1-mesa-glx [ i386 ] < none -> 9.0-0ubuntu1 > ( libs )
Broken libgl1-mesa-dri-lts-raring:i386 Depends on libglapi-mesa-lts-raring [ i386 ] < 9.1.7-1ubuntu2~precise1 > ( libs )
Broken xserver-xorg-video-all:amd64 Depends on xserver-xorg-video-vmware [ amd64 ] < none -> 1:12.0.1-1ubuntu1.1 > ( x11 )
Broken ia32-libs:amd64 Depends on ia32-libs-multiarch [ amd64 ] < none > ( none )
Broken libgl1-mesa-dri-lts-raring:amd64 Depends on libglapi-mesa-lts-raring [ amd64 ] < 9.1.7-1ubuntu2~precise1 > ( libs )
Broken libglapi-mesa-lts-raring:amd64 Conflicts on libglapi-mesa [ amd64 ] < none -> 9.0-0ubuntu1 > ( libs )
Broken libglapi-mesa-lts-raring:amd64 Conflicts on libglapi-mesa [ i386 ] < none -> 9.0-0ubuntu1 > ( libs )
Broken libgl1-mesa-glx:i386 Depends on libglapi-mesa [ i386 ] < none -> 9.0-0ubuntu1 > ( libs ) (= 9.0-0ubuntu1)
Broken libgl1-mesa-dev:amd64 Depends on libgl1-mesa-glx [ amd64 ] < none -> 9.0-0ubuntu1 > ( libs ) (= 8.0.4-0ubuntu0.7)
Broken libgl1-mesa-dev:amd64 Depends on libgl1-mesa-glx-lts-quantal [ amd64 ] < none -> 9.0.3-0ubuntu0.4~precise1 > ( libs )
Broken xserver-xorg:amd64 Conflicts on xorg-renamed-package [ amd64 ] < none > ( none )
Broken libglu1-mesa:i386 Depends on libgl1-mesa-glx [ i386 ] < none -> 9.0-0ubuntu1 > ( libs )
Broken libglu1-mesa:i386 Depends on libgl1 [ i386 ] < none > ( none )
Broken freeglut3:amd64 Depends on libgl1-mesa-glx [ amd64 ] < none -> 9.0-0ubuntu1 > ( libs )
Broken libqt4-opengl:i386 Depends on libgl1-mesa-glx [ i386 ] < none -> 9.0-0ubuntu1 > ( libs )
Broken ia32-libs-multiarch:i386 Depends on libglu1-mesa [ i386 ] < 8.0.4-0ubuntu0.7 > ( libs )
Broken libgl1-mesa-dri-lts-raring:amd64 Depends on libglapi-mesa-lts-raring [ amd64 ] < 9.1.7-1ubuntu2~precise1 > ( libs )
Broken libgl1-mesa-dev:amd64 Depends on libgl1-mesa-glx [ amd64 ] < none -> 9.0-0ubuntu1 > ( libs ) (= 8.0.4-0ubuntu0.7)
Broken libgl1-mesa-dev:amd64 Depends on libgl1-mesa-glx-lts-quantal [ amd64 ] < none -> 9.0.3-0ubuntu0.4~precise1 > ( libs )
Broken libqt4-opengl:i386 Depends on libgl1-mesa-glx [ i386 ] < none -> 9.0-0ubuntu1 > ( libs )
Broken libqt4-opengl:i386 Depends on libgl1 [ i386 ] < none > ( none )
Broken openjdk-7-jre:amd64 Depends on libgl1-mesa-glx [ amd64 ] < none -> 9.0-0ubuntu1 > ( libs )
Broken libgl1-mesa-dri-lts-raring:i386 Depends on libglapi-mesa-lts-raring [ i386 ] < 9.1.7-1ubuntu2~precise1 > ( libs )
Broken ia32-libs:amd64 Depends on ia32-libs-multiarch [ amd64 ] < none > ( none )
Broken libglapi-mesa-lts-quantal:amd64 Conflicts on libglapi-mesa [ amd64 ] < none -> 9.0-0ubuntu1 > ( libs )
Broken libgl1-mesa-dri-lts-quantal:amd64 Depends on libglapi-mesa-lts-quantal [ amd64 ] < none -> 9.0.3-0ubuntu0.4~precise1 > ( libs )
Broken libgl1-mesa-dri-lts-raring:amd64 Depends on libglapi-mesa-lts-raring [ amd64 ] < 9.1.7-1ubuntu2~precise1 > ( libs )
Broken libgl1-mesa-dev:amd64 Depends on libgl1-mesa-glx [ amd64 ] < none -> 9.0-0ubuntu1 > ( libs ) (= 8.0.4-0ubuntu0.7)
Broken libgl1-mesa-dev:amd64 Depends on libgl1-mesa-glx-lts-quantal [ amd64 ] < none -> 9.0.3-0ubuntu0.4~precise1 > ( libs )
Broken libgl1-mesa-dev:amd64 Depends on libgl1-mesa-glx [ amd64 ] < none -> 9.0-0ubuntu1 > ( libs ) (= 9.0-0ubuntu1)
Broken libglu1-mesa-dev:amd64 Depends on libgl1-mesa-dev [ amd64 ] < 8.0.4-0ubuntu0.7 -> 9.0-0ubuntu1 > ( libdevel )
Broken libglu1-mesa-dev:amd64 Depends on libgl1-mesa-dev-lts-quantal [ amd64 ] < none -> 9.0.3-0ubuntu0.4~precise1 > ( libdevel )
Broken libglu1-mesa-dev:amd64 Depends on libgl1-mesa-dev-lts-raring [ amd64 ] < none -> 9.1.7-1ubuntu2~precise1 > ( libdevel )
Broken libgl1-mesa-glx-lts-raring:amd64 Depends on libglapi-mesa-lts-raring [ amd64 ] < 9.1.7-1ubuntu2~precise1 > ( libs ) (= 9.1.7-1ubuntu2~precise1)
Broken xorg:amd64 Depends on libgl1-mesa-glx [ amd64 ] < none -> 9.0-0ubuntu1 > ( libs )
Broken libgl1-mesa-dev-lts-raring:amd64 Depends on libgl1-mesa-glx-lts-raring [ amd64 ] < 9.1.7-1ubuntu2~precise1 > ( libs ) (= 9.1.7-1ubuntu2~precise1)
Broken xserver-xorg-lts-raring:amd64 Conflicts on libgl1-mesa-glx [ amd64 ] < none -> 9.0-0ubuntu1 > ( libs ) (>= 0~)
Broken ia32-libs-multiarch:i386 Depends on libglapi-mesa [ i386 ] < none -> 9.0-0ubuntu1 > ( libs )
Broken skype-bin:i386 Depends on libgl1-mesa-glx [ i386 ] < none -> 9.0-0ubuntu1 > ( libs )
Broken libgl1-mesa-dri-lts-raring:amd64 Depends on libglapi-mesa-lts-raring [ amd64 ] < 9.1.7-1ubuntu2~precise1 > ( libs )
Broken libglapi-mesa-lts-raring:amd64 Conflicts on libglapi-mesa [ amd64 ] < none -> 9.0-0ubuntu1 > ( libs )
Broken libqt4-opengl-dev:amd64 Depends on libgl1-mesa-dev [ amd64 ] < 8.0.4-0ubuntu0.7 -> 9.0-0ubuntu1 > ( libdevel )
Broken libqt4-opengl-dev:amd64 Depends on libgl-dev [ amd64 ] < none > ( none )
Broken libgl1-mesa-dev:amd64 Depends on libgl1-mesa-glx [ amd64 ] < none -> 9.0-0ubuntu1 > ( libs ) (= 8.0.4-0ubuntu0.7)
Broken libgl1-mesa-dev:amd64 Depends on libgl1-mesa-glx-lts-quantal [ amd64 ] < none -> 9.0.3-0ubuntu0.4~precise1 > ( libs )
Broken libgl1-mesa-dev:amd64 Depends on libgl1-mesa-glx-lts-raring [ amd64 ] < 9.1.7-1ubuntu2~precise1 > ( libs )
Broken libgl1-mesa-dev:amd64 Depends on libgl1-mesa-glx-lts-saucy [ amd64 ] < none -> 9.2.1-1ubuntu3~precise1 > ( libs )
Broken libvisual-0.4-plugins:i386 Depends on libgl1-mesa-glx [ i386 ] < none -> 9.0-0ubuntu1 > ( libs )
Broken libvisual-0.4-plugins:i386 Depends on libgl1 [ i386 ] < none > ( none )
Broken libglu1-mesa:i386 Depends on libgl1-mesa-glx [ i386 ] < none -> 9.0-0ubuntu1 > ( libs )
Broken freeglut3:amd64 Depends on libgl1-mesa-glx [ amd64 ] < none -> 9.0-0ubuntu1 > ( libs )
Broken libglapi-mesa-lts-raring:i386 Conflicts on libglapi-mesa [ amd64 ] < none -> 9.0-0ubuntu1 > ( libs )
Broken libglapi-mesa-lts-raring:i386 Conflicts on libglapi-mesa [ i386 ] < none -> 9.0-0ubuntu1 > ( libs )
Broken xorg:amd64 Depends on xserver-xorg [ amd64 ] < none -> 1:7.6+12ubuntu2 > ( x11 ) (>= 1:7.6+12ubuntu2)
Broken xorg:amd64 Depends on libgl1-mesa-dri [ amd64 ] < none -> 9.0-0ubuntu1 > ( libs )
Broken ubuntu-desktop:amd64 Depends on xorg [ amd64 ] < 1:7.6+12ubuntu2 > ( x11 )
Broken ia32-libs:amd64 Depends on ia32-libs-multiarch [ amd64 ] < none > ( none )
Broken xserver-xorg-video-vmware:amd64 Depends on libxatracker1 [ amd64 ] < none -> 9.0-0ubuntu1 > ( libs )
Broken ia32-libs-multiarch:i386 Depends on libglapi-mesa [ i386 ] < none -> 9.0-0ubuntu1 > ( libs )
Broken skype:amd64 Depends on skype-bin [ amd64 ] < none > ( none )
Broken libgl1-mesa-glx:amd64 Depends on libglapi-mesa [ amd64 ] < none -> 9.0-0ubuntu1 > ( libs ) (= 9.0-0ubuntu1)
Broken x11-utils:amd64 Depends on libgl1-mesa-glx [ amd64 ] < none -> 9.0-0ubuntu1 > ( libs )
Broken libgl1-mesa-glx:i386 Depends on libglapi-mesa [ i386 ] < none -> 9.0-0ubuntu1 > ( libs ) (= 9.0-0ubuntu1)
Broken libgl1-mesa-dev:amd64 Depends on mesa-common-dev [ amd64 ] < 8.0.4-0ubuntu0.7 -> 9.0-0ubuntu1 > ( devel ) (= 8.0.4-0ubuntu0.7)
Broken libgl1-mesa-dev:amd64 Depends on mesa-common-dev-lts-quantal [ amd64 ] < none -> 9.0.3-0ubuntu0.4~precise1 > ( libdevel )
Broken libgl1-mesa-dev:amd64 Depends on libgl1-mesa-glx [ amd64 ] < none -> 9.0-0ubuntu1 > ( libs ) (= 8.0.4-0ubuntu0.7)
Broken libgl1-mesa-dev:amd64 Depends on libgl1-mesa-glx-lts-quantal [ amd64 ] < none -> 9.0.3-0ubuntu0.4~precise1 > ( libs )
Broken xserver-xorg:amd64 Conflicts on xorg-renamed-package [ amd64 ] < none > ( none )
Broken libvisual-0.4-plugins:amd64 Depends on libgl1-mesa-glx [ amd64 ] < none -> 9.0-0ubuntu1 > ( libs )
Broken libglu1-mesa:i386 Depends on libgl1-mesa-glx [ i386 ] < none -> 9.0-0ubuntu1 > ( libs )
Broken libgl1-mesa-dri-lts-raring:i386 Depends on libglapi-mesa-lts-raring [ i386 ] < 9.1.7-1ubuntu2~precise1 > ( libs )
Broken xserver-xorg-video-all:amd64 Depends on xserver-xorg-video-vmware [ amd64 ] < none -> 1:12.0.1-1ubuntu1.1 > ( x11 )
Broken ia32-libs:amd64 Depends on ia32-libs-multiarch [ amd64 ] < none > ( none )
Broken libgl1-mesa-dri-lts-raring:amd64 Depends on libglapi-mesa-lts-raring [ amd64 ] < 9.1.7-1ubuntu2~precise1 > ( libs )
Broken libglapi-mesa-lts-raring:amd64 Conflicts on libglapi-mesa [ amd64 ] < none -> 9.0-0ubuntu1 > ( libs )
Broken libglapi-mesa-lts-raring:amd64 Conflicts on libglapi-mesa [ i386 ] < none -> 9.0-0ubuntu1 > ( libs )
Broken libgl1-mesa-glx:i386 Depends on libglapi-mesa [ i386 ] < none -> 9.0-0ubuntu1 > ( libs ) (= 9.0-0ubuntu1)
Broken libgl1-mesa-dev:amd64 Depends on libgl1-mesa-glx [ amd64 ] < none -> 9.0-0ubuntu1 > ( libs ) (= 8.0.4-0ubuntu0.7)
Broken libgl1-mesa-dev:amd64 Depends on libgl1-mesa-glx-lts-quantal [ amd64 ] < none -> 9.0.3-0ubuntu0.4~precise1 > ( libs )
Broken xserver-xorg:amd64 Conflicts on xorg-renamed-package [ amd64 ] < none > ( none )
Broken libglu1-mesa:i386 Depends on libgl1-mesa-glx [ i386 ] < none -> 9.0-0ubuntu1 > ( libs )
Broken libglu1-mesa:i386 Depends on libgl1 [ i386 ] < none > ( none )
Broken freeglut3:amd64 Depends on libgl1-mesa-glx [ amd64 ] < none -> 9.0-0ubuntu1 > ( libs )
Broken libqt4-opengl:i386 Depends on libgl1-mesa-glx [ i386 ] < none -> 9.0-0ubuntu1 > ( libs )
Broken ia32-libs-multiarch:i386 Depends on libglu1-mesa [ i386 ] < 8.0.4-0ubuntu0.7 > ( libs )
Broken libgl1-mesa-dri-lts-raring:amd64 Depends on libglapi-mesa-lts-raring [ amd64 ] < 9.1.7-1ubuntu2~precise1 > ( libs )
Broken libgl1-mesa-dev:amd64 Depends on libgl1-mesa-glx [ amd64 ] < none -> 9.0-0ubuntu1 > ( libs ) (= 8.0.4-0ubuntu0.7)
Broken libgl1-mesa-dev:amd64 Depends on libgl1-mesa-glx-lts-quantal [ amd64 ] < none -> 9.0.3-0ubuntu0.4~precise1 > ( libs )
Broken libqt4-opengl:i386 Depends on libgl1-mesa-glx [ i386 ] < none -> 9.0-0ubuntu1 > ( libs )
Broken libqt4-opengl:i386 Depends on libgl1 [ i386 ] < none > ( none )
Broken openjdk-7-jre:amd64 Depends on libgl1-mesa-glx [ amd64 ] < none -> 9.0-0ubuntu1 > ( libs )
Broken libgl1-mesa-dri-lts-raring:i386 Depends on libglapi-mesa-lts-raring [ i386 ] < 9.1.7-1ubuntu2~precise1 > ( libs )
Broken ia32-libs:amd64 Depends on ia32-libs-multiarch [ amd64 ] < none > ( none )
Broken libglapi-mesa-lts-quantal:amd64 Conflicts on libglapi-mesa [ amd64 ] < none -> 9.0-0ubuntu1 > ( libs )
Broken libgl1-mesa-dri-lts-quantal:amd64 Depends on libglapi-mesa-lts-quantal [ amd64 ] < none -> 9.0.3-0ubuntu0.4~precise1 > ( libs )
Broken libgl1-mesa-dri-lts-raring:amd64 Depends on libglapi-mesa-lts-raring [ amd64 ] < 9.1.7-1ubuntu2~precise1 > ( libs )
Broken libgl1-mesa-dev:amd64 Depends on libgl1-mesa-glx [ amd64 ] < none -> 9.0-0ubuntu1 > ( libs ) (= 8.0.4-0ubuntu0.7)
Broken libgl1-mesa-dev:amd64 Depends on libgl1-mesa-glx-lts-quantal [ amd64 ] < none -> 9.0.3-0ubuntu0.4~precise1 > ( libs )
Broken libgl1-mesa-dev:amd64 Depends on libgl1-mesa-glx [ amd64 ] < none -> 9.0-0ubuntu1 > ( libs ) (= 9.0-0ubuntu1)
Broken libglu1-mesa-dev:amd64 Depends on libgl1-mesa-dev [ amd64 ] < 8.0.4-0ubuntu0.7 -> 9.0-0ubuntu1 > ( libdevel )
Broken libglu1-mesa-dev:amd64 Depends on libgl1-mesa-dev-lts-quantal [ amd64 ] < none -> 9.0.3-0ubuntu0.4~precise1 > ( libdevel )
Broken libglu1-mesa-dev:amd64 Depends on libgl1-mesa-dev-lts-raring [ amd64 ] < none -> 9.1.7-1ubuntu2~precise1 > ( libdevel )
Broken libgl1-mesa-glx-lts-raring:amd64 Depends on libglapi-mesa-lts-raring [ amd64 ] < 9.1.7-1ubuntu2~precise1 > ( libs ) (= 9.1.7-1ubuntu2~precise1)
Broken xorg:amd64 Depends on libgl1-mesa-glx [ amd64 ] < none -> 9.0-0ubuntu1 > ( libs )
Broken libgl1-mesa-dev-lts-raring:amd64 Depends on libgl1-mesa-glx-lts-raring [ amd64 ] < 9.1.7-1ubuntu2~precise1 > ( libs ) (= 9.1.7-1ubuntu2~precise1)
Broken xserver-xorg-lts-raring:amd64 Conflicts on libgl1-mesa-glx [ amd64 ] < none -> 9.0-0ubuntu1 > ( libs ) (>= 0~)
Broken ia32-libs-multiarch:i386 Depends on libglapi-mesa [ i386 ] < none -> 9.0-0ubuntu1 > ( libs )
Broken skype-bin:i386 Depends on libgl1-mesa-glx [ i386 ] < none -> 9.0-0ubuntu1 > ( libs )
Broken libgl1-mesa-dri-lts-raring:amd64 Depends on libglapi-mesa-lts-raring [ amd64 ] < 9.1.7-1ubuntu2~precise1 > ( libs )
Broken libglapi-mesa-lts-raring:amd64 Conflicts on libglapi-mesa [ amd64 ] < none -> 9.0-0ubuntu1 > ( libs )
Broken libqt4-opengl-dev:amd64 Depends on libgl1-mesa-dev [ amd64 ] < 8.0.4-0ubuntu0.7 -> 9.0-0ubuntu1 > ( libdevel )
Broken libqt4-opengl-dev:amd64 Depends on libgl-dev [ amd64 ] < none > ( none )
Broken libgl1-mesa-dev:amd64 Depends on libgl1-mesa-glx [ amd64 ] < none -> 9.0-0ubuntu1 > ( libs ) (= 8.0.4-0ubuntu0.7)
Broken libgl1-mesa-dev:amd64 Depends on libgl1-mesa-glx-lts-quantal [ amd64 ] < none -> 9.0.3-0ubuntu0.4~precise1 > ( libs )
Broken libgl1-mesa-dev:amd64 Depends on libgl1-mesa-glx-lts-raring [ amd64 ] < 9.1.7-1ubuntu2~precise1 > ( libs )
Broken libgl1-mesa-dev:amd64 Depends on libgl1-mesa-glx-lts-saucy [ amd64 ] < none -> 9.2.1-1ubuntu3~precise1 > ( libs )
Broken libvisual-0.4-plugins:i386 Depends on libgl1-mesa-glx [ i386 ] < none -> 9.0-0ubuntu1 > ( libs )
Broken libvisual-0.4-plugins:i386 Depends on libgl1 [ i386 ] < none > ( none )
Broken libglu1-mesa:i386 Depends on libgl1-mesa-glx [ i386 ] < none -> 9.0-0ubuntu1 > ( libs )
Broken freeglut3:amd64 Depends on libgl1-mesa-glx [ amd64 ] < none -> 9.0-0ubuntu1 > ( libs )
Broken libglapi-mesa-lts-raring:i386 Conflicts on libglapi-mesa [ amd64 ] < none -> 9.0-0ubuntu1 > ( libs )
Broken libglapi-mesa-lts-raring:i386 Conflicts on libglapi-mesa [ i386 ] < none -> 9.0-0ubuntu1 > ( libs )
Broken xorg:amd64 Depends on xserver-xorg [ amd64 ] < none -> 1:7.6+12ubuntu2 > ( x11 ) (>= 1:7.6+12ubuntu2)
Broken xorg:amd64 Depends on libgl1-mesa-dri [ amd64 ] < none -> 9.0-0ubuntu1 > ( libs )
Broken ubuntu-desktop:amd64 Depends on xorg [ amd64 ] < 1:7.6+12ubuntu2 > ( x11 )
Broken ia32-libs:amd64 Depends on ia32-libs-multiarch [ amd64 ] < none > ( none )
Broken xserver-xorg-video-vmware:amd64 Depends on libxatracker1 [ amd64 ] < none -> 9.0-0ubuntu1 > ( libs )
Broken ia32-libs-multiarch:i386 Depends on libglapi-mesa [ i386 ] < none -> 9.0-0ubuntu1 > ( libs )
Broken skype:amd64 Depends on skype-bin [ amd64 ] < none > ( none )
Broken libgl1-mesa-glx:amd64 Depends on libglapi-mesa [ amd64 ] < none -> 9.0-0ubuntu1 > ( libs ) (= 9.0-0ubuntu1)
Broken x11-utils:amd64 Depends on libgl1-mesa-glx [ amd64 ] < none -> 9.0-0ubuntu1 > ( libs )
Broken libgl1-mesa-glx:i386 Depends on libglapi-mesa [ i386 ] < none -> 9.0-0ubuntu1 > ( libs ) (= 9.0-0ubuntu1)
Broken libgl1-mesa-dev:amd64 Depends on mesa-common-dev [ amd64 ] < 8.0.4-0ubuntu0.7 -> 9.0-0ubuntu1 > ( devel ) (= 8.0.4-0ubuntu0.7)
Broken libgl1-mesa-dev:amd64 Depends on mesa-common-dev-lts-quantal [ amd64 ] < none -> 9.0.3-0ubuntu0.4~precise1 > ( libdevel )
Broken libgl1-mesa-dev:amd64 Depends on libgl1-mesa-glx [ amd64 ] < none -> 9.0-0ubuntu1 > ( libs ) (= 8.0.4-0ubuntu0.7)
Broken libgl1-mesa-dev:amd64 Depends on libgl1-mesa-glx-lts-quantal [ amd64 ] < none -> 9.0.3-0ubuntu0.4~precise1 > ( libs )
Broken xserver-xorg:amd64 Conflicts on xorg-renamed-package [ amd64 ] < none > ( none )
Broken libvisual-0.4-plugins:amd64 Depends on libgl1-mesa-glx [ amd64 ] < none -> 9.0-0ubuntu1 > ( libs )
Broken libglu1-mesa:i386 Depends on libgl1-mesa-glx [ i386 ] < none -> 9.0-0ubuntu1 > ( libs )
Broken libgl1-mesa-dri-lts-raring:i386 Depends on libglapi-mesa-lts-raring [ i386 ] < 9.1.7-1ubuntu2~precise1 > ( libs )
Broken xserver-xorg-video-all:amd64 Depends on xserver-xorg-video-vmware [ amd64 ] < none -> 1:12.0.1-1ubuntu1.1 > ( x11 )
Broken ia32-libs:amd64 Depends on ia32-libs-multiarch [ amd64 ] < none > ( none )
Broken libgl1-mesa-dri-lts-raring:amd64 Depends on libglapi-mesa-lts-raring [ amd64 ] < 9.1.7-1ubuntu2~precise1 > ( libs )
Broken libglapi-mesa-lts-raring:amd64 Conflicts on libglapi-mesa [ amd64 ] < none -> 9.0-0ubuntu1 > ( libs )
Broken libglapi-mesa-lts-raring:amd64 Conflicts on libglapi-mesa [ i386 ] < none -> 9.0-0ubuntu1 > ( libs )
Broken libgl1-mesa-glx:i386 Depends on libglapi-mesa [ i386 ] < none -> 9.0-0ubuntu1 > ( libs ) (= 9.0-0ubuntu1)
Broken libgl1-mesa-dev:amd64 Depends on libgl1-mesa-glx [ amd64 ] < none -> 9.0-0ubuntu1 > ( libs ) (= 8.0.4-0ubuntu0.7)
Broken libgl1-mesa-dev:amd64 Depends on libgl1-mesa-glx-lts-quantal [ amd64 ] < none -> 9.0.3-0ubuntu0.4~precise1 > ( libs )
Broken xserver-xorg:amd64 Conflicts on xorg-renamed-package [ amd64 ] < none > ( none )
Broken libglu1-mesa:i386 Depends on libgl1-mesa-glx [ i386 ] < none -> 9.0-0ubuntu1 > ( libs )
Broken libglu1-mesa:i386 Depends on libgl1 [ i386 ] < none > ( none )
Broken freeglut3:amd64 Depends on libgl1-mesa-glx [ amd64 ] < none -> 9.0-0ubuntu1 > ( libs )
Broken libqt4-opengl:i386 Depends on libgl1-mesa-glx [ i386 ] < none -> 9.0-0ubuntu1 > ( libs )
Broken ia32-libs-multiarch:i386 Depends on libglu1-mesa [ i386 ] < 8.0.4-0ubuntu0.7 > ( libs )
Broken libgl1-mesa-dri-lts-raring:amd64 Depends on libglapi-mesa-lts-raring [ amd64 ] < 9.1.7-1ubuntu2~precise1 > ( libs )
Broken libgl1-mesa-dev:amd64 Depends on libgl1-mesa-glx [ amd64 ] < none -> 9.0-0ubuntu1 > ( libs ) (= 8.0.4-0ubuntu0.7)
Broken libgl1-mesa-dev:amd64 Depends on libgl1-mesa-glx-lts-quantal [ amd64 ] < none -> 9.0.3-0ubuntu0.4~precise1 > ( libs )
Broken libqt4-opengl:i386 Depends on libgl1-mesa-glx [ i386 ] < none -> 9.0-0ubuntu1 > ( libs )
Broken libqt4-opengl:i386 Depends on libgl1 [ i386 ] < none > ( none )
Broken openjdk-7-jre:amd64 Depends on libgl1-mesa-glx [ amd64 ] < none -> 9.0-0ubuntu1 > ( libs )
Broken libgl1-mesa-dri-lts-raring:i386 Depends on libglapi-mesa-lts-raring [ i386 ] < 9.1.7-1ubuntu2~precise1 > ( libs )
Broken ia32-libs:amd64 Depends on ia32-libs-multiarch [ amd64 ] < none > ( none )
Broken libglapi-mesa-lts-quantal:amd64 Conflicts on libglapi-mesa [ amd64 ] < none -> 9.0-0ubuntu1 > ( libs )
Broken libgl1-mesa-dri-lts-quantal:amd64 Depends on libglapi-mesa-lts-quantal [ amd64 ] < none -> 9.0.3-0ubuntu0.4~precise1 > ( libs )
Broken libgl1-mesa-dri-lts-raring:amd64 Depends on libglapi-mesa-lts-raring [ amd64 ] < 9.1.7-1ubuntu2~precise1 > ( libs )
Broken libgl1-mesa-dev:amd64 Depends on libgl1-mesa-glx [ amd64 ] < none -> 9.0-0ubuntu1 > ( libs ) (= 8.0.4-0ubuntu0.7)
Broken libgl1-mesa-dev:amd64 Depends on libgl1-mesa-glx-lts-quantal [ amd64 ] < none -> 9.0.3-0ubuntu0.4~precise1 > ( libs )

```


I'm running ubunutu 12.04 with gnome instead of unity.


Anyone can help me?

Thank you

---

### Post by grahammechanical on 2014-02-19
May I suggest that you try again and this time do not accept a partial upgrade. Just click Continue. There are four reasons listed as to why we get that offer of a partial upgrade.

1) A previous upgrade which did not complete
2) Problems with some of the installed software
3) Unoffical software packages not provided by Ubuntu
4) Normal changes of a pre-release version of Ubuntu.

I would suggest that number 3 fits your situation. How did you install Steam? Did you search for "Valve " in the Ubuntu Software Centre? That has something called Valve's Steam Digital Software Delivery System. That should run on Ubuntu. Did you install Steam OS?

[https://wiki.ubuntu.com/Valve](https://wiki.ubuntu.com/Valve)

Regards.

---

### Post by Bisneff on 2014-02-28
HI

Thank you for the answer.

i'd just added the PPA in the guide in the firts post. I install Steam writting "steam" in the software center, but when I run it, say that I need new ppa to make it work better. Then I follow the guide and now I have this trouble.
Here I put a screenshot, maybe could help.

[IMG]https://dl.dropboxusercontent.com/u/41646478/Screenshot%20from%202014-03-01%2001%3A23%3A58.png[/IMG]

Thanks for your support

---

