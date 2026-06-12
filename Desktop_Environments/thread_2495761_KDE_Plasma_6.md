---
title: "KDE Plasma 6"
date: 2024-02-29
forum: Desktop Environments
---

### Post by 3vi1 on 2024-02-29
I'm thinking about building it from source to give it a shot.

Is there an easier way/PPA that I may be unaware of?  

I used to build KDE from source repeatedly back in the days I was using Mandrake.  I may do it anyway for nostalgia's sake.

Thanks!

---

### Post by mahmoud-bahaa on 2024-02-29
Nop no ppa of sort yet and it won't even ship with ubuntu 24.04 but I am in progress of builting it on (k)ubuntu 24.04 and this the progress so far:


[LIST=1]
[*]Qt6 is outdated in ubuntu 24.04 (it has 6.4 while you need 6.5+) The best/easiest option is to either :
[LIST]
[*]The easy way: Use qt-online-installer and download/install ONLY qt 6.6 binaries (no need for any other component)  [https://download.qt.io/official_releases/qt/6.6/6.6.2/single/](https://download.qt.io/official_releases/qt/6.6/6.6.2/single/)
[*]The hard way: built it from source: [https://doc.qt.io/qt-6/linux-building.html](https://doc.qt.io/qt-6/linux-building.html) (had some issue with it so gave up on that)
[/LIST]

[*]Whatever you choose you need to add ```
export PATH=Path_To_QT/Qt/6.6.2/gcc_64/bin/:"$PATH"
``` to **basrc** or **zshrc** or whatever shell you are using
[*]Install kde-builder: [https://invent.kde.org/sdk/kde-builder#installation](https://invent.kde.org/sdk/kde-builder#installation) (the section named **Using virtual environment) **I needed to do the following adjustment though
[LIST=1]
[*]Make sure you have python3.11. Can be easily installed by sudo apt install python3.11-dev (pytho 3.12 or 3.10 didn't work)
[*]other packages you need to install: ```
sudo apt install build-essential cmake libglib2.0 libdbus-1-dev libavfilter-dev libva-dev libdisplay-info-dev xdotool libcups2-dev sassc
```
[*]Other packages you **may** need to install (Not sure since these was installed when i was attempting to build qt6 from source before aborting and just install from installer) mentioned here [https://doc.qt.io/qt-6/linux-requirements.html](https://doc.qt.io/qt-6/linux-requirements.html)  ```
sudo apt install libfontconfig1-dev libfreetype6-dev libx11-dev libx11-xcb-dev libxext-dev libxfixes-dev libxi-dev libxrender-dev libxcb1-dev libxcb-cursor-dev libxcb-glx0-dev libxcb-keysyms1-dev libxcb-image0-dev libxcb-shm0-dev libxcb-icccm4-dev libxcb-sync-dev libxcb-xfixes0-dev libxcb-shape0-dev libxcb-randr0-dev libxcb-render-util0-dev libxcb-util-dev libxcb-xinerama0-dev libxcb-xkb-dev libxkbcommon-dev libxkbcommon-x11-dev
```
[*]install pipx (the guide says you can use pip but i have found it had problems and needed to use pipx) ```
sudo apt install pipx
pipx install pipenv
export PATH=~/.local/bin:"$PATH" #add it to bashrc/zshrc

```
[*]continue with the kde guide but the cmake options they mention need added is only found after the command ```
kde-builder --generate-config
```
[*]You may have to do:
```
git config --global --add url.http://invent.kde.org/.insteadOf kde:
git config --global --add url.ssh://git@invent.kde.org/.pushInsteadOf kde:

``` If you have problems with ```
kde-builder --install-distro-packages
```
[/LIST]

[*]Build Plasma :) [https://community.kde.org/Get_Involved/development/Build_software_with_kde-builder](https://community.kde.org/Get_Involved/development/Build_software_with_kde-builder) ```
kde-builder workspace
```
[/LIST]

To Be Updated

---

### Post by TenPlus1 on 2024-03-01
One of the easiest ways to try out Plasma 6 is to grab KDE Neon distro's daily iso which is built on Ubuntu with Plasma 6 included.  Then hopefully 24.04 when it's released will include the latest stable release when it comes out in April.

---

### Post by 3vi1 on 2024-03-01
Oh wow!  Thanks for the instructions; you saved me quite a bit of time figuring that all out for myself.

I'm giving it a quick test now, building kcalc before I kick off the whole workspace build.

---

### Post by 3vi1 on 2024-03-01
> **TenPlus1 said:**
> One of the easiest ways to try out Plasma 6 is to grab KDE Neon distro's daily iso which is built on Ubuntu with Plasma 6 included.  Then hopefully 24.04 when it's released will include the latest stable release when it comes out in April.

No, we test in production with our own desktops like real men!  :)

---

### Post by #&amp;thj^% on 2024-03-02
No matter "your preferred method of getting there" once you arrive it's pretty yummy.;)
Compiled for Arch A few bugs to be expected, KDE-Neon is very nice, but fewer bugs noticed.
```
apt policy plasma-desktop
plasma-desktop:
  Installed: 4:6.0.0+p22.04+vstable+git20240302.0456-0
  Candidate: 4:6.0.0+p22.04+vstable+git20240302.0456-0
  Version table:
 *** 4:6.0.0+p22.04+vstable+git20240302.0456-0 500
        500 http://archive.neon.kde.org/testing jammy/main amd64 Packages
        100 /var/lib/dpkg/status
     4:5.24.7-0ubuntu0.1 500
        500 http://archive.ubuntu.com/ubuntu jammy-updates/universe amd64 Packages
     4:5.24.4-0ubuntu1 500
        500 http://archive.ubuntu.com/ubuntu jammy/universe amd64 Packages

```
It won't hit in the repo's until midway through 24.10, so you have some time to wait.
Good Luck though keep us real men posted......LOL

---

### Post by 3vi1 on 2024-03-03
I went to compile it last night and had it error-out when it got to appstream (47 packages in...):

```
[207/276] Compiling C object src/libappstream.so.1.0.3.p/as-validator.c.o
FAILED: src/libappstream.so.1.0.3.p/as-validator.c.o 
ccache cc -Isrc/libappstream.so.1.0.3.p -Isrc/ -I../../src/appstream/src -I/usr/include -I. -I../../src/appstream -Isubprojects/libxmlb/src -I../../src/appstream/subprojects/libxmlb/src -Isrc -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/x86_64-linux-gnu -I/usr/include/libmount -I/usr/include/blkid -I/usr/include/libxml2 -fdiagnostics-color=always -D_FILE_OFFSET_BITS=64 -Wall -Winvalid-pch -std=c11 -O0 -g -Werror=shadow -Werror=empty-body -Werror=strict-prototypes -Werror=missing-prototypes -Werror=implicit-function-declaration -Werror=pointer-arith -Werror=missing-declarations -Werror=return-type -Werror=int-conversion -Werror=incompatible-pointer-types -Werror=misleading-indentation -Werror=missing-include-dirs -Werror=declaration-after-statement -Werror=format-security -Wno-missing-field-initializers -Wno-error=missing-field-initializers -Wno-unused-parameter -Wno-error=unused-parameter -D_POSIX_C_SOURCE=201710L -DAS_COMPILATION -fPIC -pthread -MD -MQ src/libappstream.so.1.0.3.p/as-validator.c.o -MF src/libappstream.so.1.0.3.p/as-validator.c.o.d -o src/libappstream.so.1.0.3.p/as-validator.c.o -c ../../src/appstream/src/as-validator.c
../../src/appstream/src/as-validator.c: In function &#8216;as_validator_check_web_url&#8217;:
../../src/appstream/src/as-validator.c:411:17: error: format not a string literal and no format arguments [-Werror=format-security]
  411 |                 as_validator_add_issue (validator, node, "url-uses-ftp", url);
      |                 ^~~~~~~~~~~~~~~~~~~~~~
```

Are you guys using a specific version of gcc?  I was trying with version 13.2.0 & version 14.0.1.

Kcalc & Dolphin build fine.

---

### Post by #&amp;thj^% on 2024-03-03
I'm still reading your new post, but: 
```
gcc --version
gcc (Ubuntu 11.4.0-1ubuntu1~22.04) 11.4.0
Copyright (C) 2021 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.


``` 
i wonder if 24.04 is too new to compile plasma6, IJDK.....Kcalc & Dolphin are about the easiest to compile successfully.
Kioslave and those related are the real Buggers.
```
apt depends plasma-desktop plasma-session
plasma-desktop
  Depends: breeze
  Depends: ibus-data
  Depends: kactivitymanagerd
  Depends: kde-cli-tools
  Depends: kf6-baloo (>= 6.0.0+p22.04+vstable+git20240302.0349)
  Depends: kf6-kdeclarative
  Depends: kf6-kded
  Depends: kf6-kio (>= 6.0.0+p22.04+vstable+git20240302.0319)
  Depends: kf6-kirigami2
  Depends: kf6-kwindowsystem (>= 6.0.0+p22.04+vstable+git20240302.0048)
  Depends: kf6-solid (>= 6.0.0+p22.04+vstable+git20240302.0106)
  Depends: libplasma6 (>= 6.0.0+p22.04+vstable+git20240302.0357)
  Depends: oxygen-sounds
  Depends: plasma-activities (>= 6.0.0+p22.04+vstable+git20240223.0938)
  Depends: plasma-integration
  Depends: plasma-thunderbolt
  Depends: plasma-workspace (>= 4:6.0.0+p22.04+vstable+git20240226.0341)
  Depends: polkit-kde-agent-1
  Depends: <python3:any>
    python3
  Depends: qml6-module-org-kde-pipewire
  Depends: qml6-module-qt-labs-folderlistmodel
  Depends: qml6-module-qt-labs-platform
  Depends: qml6-module-qt-labs-settings
  Depends: qml6-module-qtquick-dialogs
  Depends: kaccounts-integration (>= 4:24.02.0+p22.04+vstable+git20240301.0120)
  Depends: kf6-kauth (>= 6.0.0+p22.04+vstable+git20240302.0127)
  Depends: kf6-kbookmarks (>= 6.0.0+p22.04+vstable+git20240302.0222)
  Depends: kf6-kcmutils (>= 6.0.0+p22.04+vstable+git20240302.0336)
  Depends: kf6-kcodecs (>= 6.0.0+p22.04+vstable+git20240302.0102)
  Depends: kf6-kcompletion (>= 6.0.0+p22.04+vstable+git20240302.0127)
  Depends: kf6-kconfig (>= 6.0.0+p22.04+vstable+git20240302.0102)
  Depends: kf6-kconfigwidgets (>= 6.0.0+p22.04+vstable+git20240302.0157)
  Depends: kf6-kcoreaddons (>= 6.0.0+p22.04+vstable+git20240302.0103)
  Depends: kf6-kcrash (>= 6.0.0+p22.04+vstable+git20240221.1736)
  Depends: kf6-kdbusaddons (>= 6.0.0+p22.04+vstable+git20240302.0103)
  Depends: kf6-kglobalaccel (>= 6.0.0+p22.04+vstable+git20240302.0131)
  Depends: kf6-kguiaddons (>= 6.0.0+p22.04+vstable+git20240225.0922)
  Depends: kf6-ki18n (>= 6.0.0+p22.04+vstable+git20240302.0105)
  Depends: kf6-kiconthemes (>= 6.0.0+p22.04+vstable+git20240302.0221)
  Depends: kf6-kitemviews (>= 6.0.0+p22.04+vstable+git20240302.0105)
  Depends: kf6-kjobwidgets (>= 6.0.0+p22.04+vstable+git20240302.0158)
  Depends: kf6-knewstuff (>= 6.0.0+p22.04+vstable+git20240302.0336)
  Depends: kf6-knotifications (>= 6.0.0+p22.04+vstable+git20240302.0128)
  Depends: kf6-knotifyconfig (>= 6.0.0+p22.04+vstable+git20240302.0336)
  Depends: kf6-kpackage (>= 6.0.0+p22.04+vstable+git20240302.0159)
  Depends: kf6-krunner (>= 6.0.0+p22.04+vstable+git20240227.1020)
  Depends: kf6-kservice (>= 6.0.0+p22.04+vstable+git20240302.0159)
  Depends: kf6-ksvg (>= 6.0.0+p22.04+vstable+git20240302.0150)
  Depends: kf6-kwidgetsaddons (>= 6.0.0+p22.04+vstable+git20240302.0045)
  Depends: kf6-kxmlgui (>= 6.0.0+p22.04+vstable+git20240302.0302)
  Depends: kf6-sonnet (>= 6.0.0+p22.04+vstable+git20240302.0106)
  Depends: libaccounts-qt6-1 (>= 1.16.0nicofee20240222+p22.04+vstable+git20240222.1552)
  Depends: libc6 (>= 2.34)
  Depends: libcanberra0 (>= 0.2)
  Depends: libglib2.0-0 (>= 2.37.3)
  Depends: libibus-1.0-5 (>= 1.5.1)
  Depends: libicu70 (>= 70.1-1~)
  Depends: libksysguard (>= 4:6.0.0+p22.04+vstable+git20240302.0429)
  Depends: libpackagekitqt6 (>= 1.1.1)
  Depends: libscim8v5 (>= 1.4)
  Depends: libsdl2-2.0-0 (>= 2.28.5+dfsg)
  Depends: libstdc++6 (>= 5)
  Depends: libwayland-client0 (>= 1.2.0)
  Depends: libx11-6 (>= 2:1.2.99.901)
  Depends: libx11-xcb1 (>= 2:1.7.5)
  Depends: libxcb-keysyms1 (>= 0.4.0)
  Depends: libxcb-record0
  Depends: libxcb-xkb1
  Depends: libxcb1
  Depends: libxcursor1 (>> 1.1.2)
  Depends: libxi6 (>= 2:1.2.99.4)
  Depends: libxkbcommon0 (>= 0.5.0)
  Depends: libxkbfile1 (>= 1:1.1.0)
  Depends: plasma-activities-stats (>= 6.0.0+p22.04+vstable+git20240223.0942)
  Depends: qt6-base (>= 6.6.2)
  Depends: qt6-declarative (>= 6.6.2)
  Depends: qt6-wayland (>= 6.6.2)
  Breaks: neon-settings-2 (<< 0.5)
  Recommends: bluedevil
  Recommends: breeze-gtk-theme
  Recommends: kde-config-gtk-style
  Recommends: kde-config-screenlocker
    kscreenlocker
  Recommends: kde-config-sddm
  Recommends: <kde-style-oxygen-qt6>
  Recommends: kgamma5
    kgamma
  Recommends: khelpcenter
  Recommends: kinfocenter
  Recommends: kio-extras
  Recommends: kmenuedit
  Recommends: kscreen
  Recommends: ksshaskpass
 |Recommends: kwin-wayland
  Recommends: kwin-x11
  Recommends: kwrited
  Recommends: libpam-kwallet-common
  Recommends: plasma-discover
  Recommends: plasma-pa
  Recommends: powerdevil
  Recommends: systemsettings
  Replaces: kde-config-touchpad
    plasma-desktop
  Replaces: neon-settings-2 (<< 0.5)
  Replaces: plasma-desktop-data
    plasma-desktop
  Replaces: user-manager
    plasma-desktop

```

Kwayland is very nice, bi-directional with nVidia.
```
inxi -G |grep wayland
  Display: wayland server: X.org v: 1.21.1.4 with: Xwayland v: 23.2.4
    compositor: kwin_wayland driver: X: loaded: amdgpu,ati,nvidia

```

---

### Post by 3vi1 on 2024-03-03
I can give it a try with gcc-11.  I'll give it a shot and do a --refresh-build in a bit, thanks!

Kio and the other modules (except the final workspace one) all seemed to be compiling fine.  I had tested using --resume-after to make sure everything else was working.

EDIT:  I kicked it off, and I was correct - it was the rule-checking in newer GCC versions.  Appstream compiles fine when using gcc-11 like you suggested.  Thanks again!

---

### Post by 3vi1 on 2024-03-03
Found another issue which I think by be a bug in the kde-builder process:

When it gets to compiling the plasma-workspace, it tries to link with /usr/lib/x86_64-linux-gnu/libQt6Core5Compat.so.6 in the main system libraries instead of the path location where you pointed it to Qt 6.6.2 (/opt/Qt/6.6.2/gcc_64/lib/libQt6Core5Compat.so.6.6.2 on my system).  So, if like me you have Qt6.4 installed from the Ubuntu 24.04 repos... it's going to fail due to some missing 6.6.2 types during the link.

I got around it by copying the newer libQt6Core5Compat.so.6.6.2 dll to the main /usr/lib/x86_64-linux-gnu/ path and replacing the link for libQt6Core5Compat.so.6 to point to it.  Maybe there's a Qt env variable we could set that would fix this instead?

Waiting for the remaining 40+ to compile now....

---

### Post by 3vi1 on 2024-03-03
Found one more thing to throw into the instructions:  Looks like there's a pre-req for libvlccore-dev.  Without it, the phonon-vlc package fails to build.

---

### Post by 3vi1 on 2024-03-03
breeze-gtk seems to have a few dependencies I'm trying to figure out now...

```
-- The following RUNTIME packages have not been found:

 * GTKEngine, Pixmap/Pixbuf theme engine for GTK 2, <http://www.gtk.org/>
   Required for GTK 2 theme

-- The following REQUIRED packages have not been found:

 * PythonCairo
   Required to render assets

```

---

### Post by mechanical2 on 2024-03-03
I got Plasma 6 (more or less) working on Kubuntu 24.04. Was quite bit a challenge for me.

Began with building Qt6 from source ("the hard way" as mentioned in the post of [mahmoud-bahaa)]("https://ubuntuforums.org/member.php?u=2186230"), 24.04 delivers only qt6.4 - but at least 6.6 is needed.
[https://doc.qt.io/qt-6/linux-building.html](https://doc.qt.io/qt-6/linux-building.html)
[https://wiki.qt.io/Building_Qt_6_from_Git](https://wiki.qt.io/Building_Qt_6_from_Git)

While trying to build with kde-builder studying log-files and finding   out which packages were missing, i got stuck while building discover.
The problem is building of snapd-backend, somewhere i read it has something to do with building Qt5 instead Qt6, whatever.
I could fix it in this way (I don't use snap in general, prefering flatpak):

 Comment out all snapd-stuff in the file: ```
 "whatever path"/kde/src/discover/libdiscover/backends/CMakeLists.txt 


```

My file looks like this:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293457&stc=1[/IMG]

Then it was possible to build discover with kde-build, which is needed for plasma-workspace.

Good luck.

---

### Post by #&amp;thj^% on 2024-03-03
The first not found might need this:
```
sudo apt install gtk2-engines-pixbuf

```
And the second not found
```
sudo apt install pycairo
```
Your not out of the woods yet.

---

### Post by mechanical2 on 2024-03-03
I installed these packages, I'm not sure if really all are needed, at least it worked.
```

sudo apt-get install libfontconfig1-dev libx11-xcb-dev libxext-dev libxfixes-dev libxi-dev libxrender-dev libxcb1-dev libxcb-cursor-dev libxcb-glx0-dev libxcb-keysyms1-dev libxcb-image0-dev libxcb-shm0-dev libxcb-icccm4-dev libxcb-sync-dev libxcb-xfixes0-dev libxcb-shape0-dev libxcb-randr0-dev libxcb-render-util0-dev libxcb-util-dev libxcb-xinerama0-dev libxcb-xkb-dev libxkbcommon-dev libxkbcommon-x11-dev libxcb-dri2-0-dev libxcb-dri3-0-dev libxcb-xinput-dev

sudo apt-get install libdrm-dev libcups2-dev libcupsfilters-dev libcupsimage2-dev libxkbcommon-dev libdbus-1-dev libdbus-glib-1-dev libnss3-dev libnspr4-dev libfl-dev flex libfl2 bison libbison-dev m4 libwayland-egl-backend-dev libhunspell-dev gperf nodejs clang libclang-cpp-dev libicu-dev libncurses-dev libxml2-dev llvm-17-dev ninja-build cmake libblkid-dev libbrotli-dev libclang-dev libevdev-dev libffi-dev libfontconfig-dev libfreetype-dev libgl-dev libglib2.0-dev libglx-dev libinput-dev libmount-dev libpcre2-dev libpng-dev libudev-dev libx11-dev libxcb1-dev uuid-dev pipenv python3.12-dev python3-pip libegl-dev qt6-wayland-dev waylandpp-dev qt6-wayland-private-dev plasma-wayland-protocols libwayland-server++1 libwayland-client++1 libwayland-client-extra++1 qt6-multimedia-dev libxshmfence-dev libxkbfile-dev  cmake-extras extra-cmake-modules python3-sentry-sdk systemd-coredump libqt6keychain1 qtkeychain-qt6-dev libpython3-all-dev chai libxxf86vm-dev libkaccounts-dev libsdl2-dev libfuse3-dev libappmenu-gtk3-parser-dev python3-flask python3-pyatspi qt6-pdf-dev qt6-sensors-dev qt6-webengine-dev qt6-webview-dev binutils-dev libcryptsetup-dev libcryptui-dev libglibmm-2.68-dev libpthread-workqueue-dev libpthreadpool-dev libcrypto++-dev
```

---

### Post by 3vi1 on 2024-03-03
> **1fallen said:**
> The first not found might need this:
```
sudo apt install gtk2-engines-pixbuf

```
And the second not found
```
sudo apt install pycairo
```
Your not out of the woods yet.

Yes - I had tried installing those two, as well as doing a pip install of pycairo and apt-installing the python3-cairo package.  No luck so far... still shows the same two errors.

---

### Post by toomasr on 2024-03-04
libappstream project seems to have a compilation issue. The bug is reported here [https://github.com/ximion/appstream/issues/614](https://github.com/ximion/appstream/issues/614)

A quick fix is commenting out those two definitions [https://github.com/ximion/appstream/commit/06d2034490726bffbf071835fcb74590203c95cb](https://github.com/ximion/appstream/commit/06d2034490726bffbf071835fcb74590203c95cb) and I was able to get it compile

---

### Post by 3vi1 on 2024-03-04
Had a few minutes this morning and found my problem:  Due to my conda setup I was pip-installing into the wrong directory (doh).  I figured it out and tested with one package, so I'll resume now and figure out what else I might still be missing.  :)

I also found you can avoid a lot of the mismatched Qt/cmake versions of your main environment if you prefix your kde-builder command with some variable overrides like so:  CMAKE_PREFIX_PATH=/opt/Qt/6.6.2/gcc_64 Qt6_DIR=/opt/Qt/6.6.2 kde-builder

---

### Post by 3vi1 on 2024-03-04
@mechanical2:  Good tip - I just hit the same snap issue with discover.  Thanks for the info!

---

### Post by #&amp;thj^% on 2024-03-04
> **3vi1 said:**
> 
I also found you can avoid a lot of the mismatched Qt/cmake versions of your main environment if you prefix your kde-builder command with some variable overrides like so:  CMAKE_PREFIX_PATH=/opt/Qt/6.6.2/gcc_64 Qt6_DIR=/opt/Qt/6.6.2 kde-builder
Nicely done.....I had to do that in Arch as well but was not sure about Kubuntu.
I'm hoping for the best outcome for you now. Your on the downhill side now.

---

### Post by 3vi1 on 2024-03-04
Success!  At least, it all built successfully.  I'll test it out tomorrow afternoon, as I have other projects going on tonight.

I noticed some additional pre-reqs for the plasma-desktop package which people might need to install.  I compile a lot of projects from source, but I'd never needed these before:
```
sudo apt install xserver-xorg-input-evdev-dev xserver-xorg-input-libinput-dev xserver-xorg-dev
```

Another issue I found (this might only affect people who aren't overriding the CMAKE/QT6 paths as I was):  Some packages (kdeplasma-addons for one, I think) depend on libicu74... but the Qt6.6.2 install only includes an older version (56, maybe).  I just took the ugly hack of relinking the relevant libicu*.so symlinks to my system's *.so.74.2 versions.  It worked, but I'm sure there's a better way.

Will give it a try tomorrow!

---

### Post by toomasr on 2024-03-05
And I was finally able to build everything and thank you for all the posts on this thread that helped me out. I did discover on multiple occasions that I was missing a dependency or with wallpapers package the install script was supposed to copy folders that were not there and I just commented out those lines.

The toughest part for me was to get this to run in the end as the typical .xinitrc or XSESSION approach to use the new startplasma-x11/wayland was not working. I stumbled on [https://nicolasfella.de/posts/building-plasma-against-qt6/](https://nicolasfella.de/posts/building-plasma-against-qt6/) that led to running:

```
run sudo ./login-sessions/install-sessions.sh
``` from the build folder to install a proper session file and my sddm picked it up and I was able to log in.

Some packages that I don't believe have been mentioned here that were needed
```
xserver-xorg-input-evdev-dev xserver-xorg-input-libinput-dev libxxf86vm-dev
```

Also when I was building QT it did compile with Qt PrintSupport but without CUPS. One of the KDE packages on the other hand depended on it and finally I got QT to build CUPS once I also installed
```
libcpdb-dev
```

For the plasma-workspace-wallpapers/CMakeLists.txt it was not able to find SafeLanding, Shell, summer_1am, Volna and one more that I don't find a note about. As the install script is trying to copy non-existent folders then feel free to comment those lines out of the txt file.

Also make sure you have enough disk space. My QT build folder was about 42GB (plus the 4GB tar file) and now I see that my KDE is 36GB.

---

### Post by Ganton on 2024-03-05
> **3vi1 said:**
> I went to compile it last night and had it error-out when it got to appstream (47 packages in...):

```
[207/276] Compiling C object src/libappstream.so.1.0.3.p/as-validator.c.o
FAILED: src/libappstream.so.1.0.3.p/as-validator.c.o 
ccache cc -Isrc/libappstream.so.1.0.3.p -Isrc/ -I../../src/appstream/src -I/usr/include -I. -I../../src/appstream -Isubprojects/libxmlb/src -I../../src/appstream/subprojects/libxmlb/src -Isrc -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/x86_64-linux-gnu -I/usr/include/libmount -I/usr/include/blkid -I/usr/include/libxml2 -fdiagnostics-color=always -D_FILE_OFFSET_BITS=64 -Wall -Winvalid-pch -std=c11 -O0 -g -Werror=shadow -Werror=empty-body -Werror=strict-prototypes -Werror=missing-prototypes -Werror=implicit-function-declaration -Werror=pointer-arith -Werror=missing-declarations -Werror=return-type -Werror=int-conversion -Werror=incompatible-pointer-types -Werror=misleading-indentation -Werror=missing-include-dirs -Werror=declaration-after-statement -Werror=format-security -Wno-missing-field-initializers -Wno-error=missing-field-initializers -Wno-unused-parameter -Wno-error=unused-parameter -D_POSIX_C_SOURCE=201710L -DAS_COMPILATION -fPIC -pthread -MD -MQ src/libappstream.so.1.0.3.p/as-validator.c.o -MF src/libappstream.so.1.0.3.p/as-validator.c.o.d -o src/libappstream.so.1.0.3.p/as-validator.c.o -c ../../src/appstream/src/as-validator.c
../../src/appstream/src/as-validator.c: In function ‘as_validator_check_web_url’:
../../src/appstream/src/as-validator.c:411:17: error: format not a string literal and no format arguments [-Werror=format-security]
  411 |                 as_validator_add_issue (validator, node, "url-uses-ftp", url);
      |                 ^~~~~~~~~~~~~~~~~~~~~~
```

Are you guys using a specific version of gcc?  I was trying with version 13.2.0 & version 14.0.1.

Kcalc & Dolphin build fine.

So it's not only me :-) . There's a bug report for Appstream: [https://github.com/ximion/appstream/issues/614](https://github.com/ximion/appstream/issues/614) 
Perhaps somebody wants to write something there...

---

### Post by Ganton on 2024-03-05
> **toomasr said:**
> [...] The toughest part for me was to get this to run in the end as the typical .xinitrc or XSESSION approach to use the new startplasma-x11/wayland was not working. I stumbled on [https://nicolasfella.de/posts/building-plasma-against-qt6/](https://nicolasfella.de/posts/building-plasma-against-qt6/) that led to running:

```
run sudo ./login-sessions/install-sessions.sh
``` from the build folder to install a proper session file and my sddm picked it up and I was able to log in.

[...]


Note: In [https://community.kde.org/Get_Involved/development/Build_software_with_kde-builder](https://community.kde.org/Get_Involved/development/Build_software_with_kde-builder) we can read some useful information like:

[I]Now it's time to make your built-from-source Plasma session accessible from the SDDM login screen. We will also copy the built-from-source DBus files into a location where they are visible to the system bus. To do this, run the following command: 
```
~/kde/build/plasma-workspace/login-sessions/install-sessions.sh
```
[/I]

---

### Post by 3vi1 on 2024-03-05
Another thing that might help some people:

After running ~/kde/build/plasma-workspace/login-sessions/install-sessions.sh, per the Getting Involved page mentioned above, I did not see the sessions in my SDDM list.  I rebooted, checked the permissions, even moved the .desktop files from /usr/local/share/* to the /usr/share/* directories with the others and they still wouldn't show up in the list of available desktop sessions.

After playing with the Exec= and TryExec= lines to no avail, I finally just took a stab and changed the Name= line to something much shorter.  I don't know if it's due to a bug with the SDDM theme I'm using (neoncity) or what, but that's what fixed the problem and got the names to show up in my list.

Now:  Anyone know how to disable the "KDE Plasma 6.1 Dev" watermark in the bottom right corner?  I feel like I'm running an unregistered version of Windows here.  :)

---

### Post by 3vi1 on 2024-03-05
This is new and unexpected:  I notice that plasmashell tries to connect to [www.ecb.europa.eu](www.ecb.europa.eu), when you're searching for things in the launcher.  A quick grep of the source reveals it's from code in kunitconversion/src/currency.cpp.  I'm not sure why the hell it would be trying to connect when all I was doing is searching for "Spectacle" from the launcher, though.  It seems like this should really be something we ought to have an option to disable up front.

[IMG]https://i.imgur.com/5eCEo9n.png[/IMG]

Other misc things I've noted:
* Logout: trying to logout from Wayland with Nvidia 550.54.14 drivers (RTX 2070 Super) ended up just blurring both my screens and not showing me any options... It doesn't seem to time out, and there's no way to get out of it short of flipping to a TTY and restarting SDDM.
* Wayland:  X11 works great... Wayland's still a stuttery mess after letting it run for a few hours.  Playing Netflix became unwatchable on either monitor due to all the jitter and dropped frames.

---

### Post by Ganton on 2024-03-05
> **3vi1 said:**
> Another thing that might help some people:

After running ~/kde/build/plasma-workspace/login-sessions/install-sessions.sh, per the Getting Involved page mentioned above, I did not see the sessions in my SDDM list.  [...]

I could see the new options, although "empty" (with no label). In [https://community.kde.org/Plasma/Plasma_6](https://community.kde.org/Plasma/Plasma_6) we can see:

[I]Known upstream issues, no fix yet:
For built-from-source dev sessions, SDDM displays empty/incorrect session titles 
    Fixed in SDDM after 0.20.0 was released [ [https://github.com/sddm/sddm/commit/5b702ae986464fe6dbc8557d4b2da725ac1ed175](https://github.com/sddm/sddm/commit/5b702ae986464fe6dbc8557d4b2da725ac1ed175) ] [...][/I]

Note: Later, SDDM 0.21.0 was released.

---

### Post by 3vi1 on 2024-03-05
I believe I too saw an empty item at first, but that went away while I tried other things to fix it, and the options only came back after I adjusted the Name attribute.

---

### Post by #&amp;thj^% on 2024-03-05
This might be the difference then:
```
apt policy sddm
sddm:
  Installed: 0.21.0+p22.04+vstable+git20240226.1033-0
  Candidate: 0.21.0+p22.04+vstable+git20240226.1033-0
  Version table:
 *** 0.21.0+p22.04+vstable+git20240226.1033-0 500

```

It ran so crappy on arch I reverted back to plasma5
But still very smooth on neon.

---

### Post by 3vi1 on 2024-03-05
> **1fallen said:**
> This might be the difference then:
```
apt policy sddm
sddm:
  Installed: 0.21.0+p22.04+vstable+git20240226.1033-0
  Candidate: 0.21.0+p22.04+vstable+git20240226.1033-0
  Version table:
 *** 0.21.0+p22.04+vstable+git20240226.1033-0 500

```

It ran so crappy on arch I reverted back to plasma5
But still very smooth on neon.

Yes, that's likely it since I have the 0.20.0-2ubuntu1 package from the Ubuntu devel repos currently installed.

When it ran crappy on Arch, was that using Wayland?  I have previously seen Wayland with Plasma5 occasionally acting like it has no hardware accelleration (nVidia driver problem, most likely), but it would not do it on every boot.

Due to the jitter and multimonitor vs. flameshot issues I was having, I'm using Plasma6 with X11 at the moment.  Other than the logoff bug I mentioned previously (maybe some other package I need to build?), it seems to be solid.

Thanks!

---

### Post by #&amp;thj^% on 2024-03-05
On Arch it just ran in a way I won't accept less than crisp some app's segfault...yada yada.

Dang that's a shame it runs the way it dose for you on Wayland, I hardly notice any difference.. BTW  did you see the bridge to X11 under hidden icons on the panel.

Nvidia here as well.
```

Device-1: NVIDIA GA107BM [GeForce RTX 3050 Ti Mobile] driver: nvidia
    v: 550.54.14

```

---

### Post by Ganton on 2024-03-06
> **Ganton said:**
> So it's not only me :-) . There's a bug report for Appstream: [https://github.com/ximion/appstream/issues/614](https://github.com/ximion/appstream/issues/614) 
Perhaps somebody wants to write something there...

That was solved today &#128077;

---

### Post by 3vi1 on 2024-03-06
> **3vi1 said:**
> Now:  Anyone know how to disable the "KDE Plasma 6.1 Dev" watermark in the bottom right corner?  I feel like I'm running an unregistered version of Windows here.  :)

I took a look at the source a couple of minutes ago and figured this one out:

Edit your ~/.config/kdeglobals file and add this under the "[General]" section:

```
HideDesktopPreviewBanner=true
```

Restart plasma and the Dev banner message will no longer be overlayed on your wallpaper.

Later!

---

### Post by 3vi1 on 2024-03-07
Anyone else have an issue with the Open File dialog being broken?

If I go to any website, for instance imgur.com, and click the New Post "Upload File" button when using a chromium based browser (which uses the system/DE file dialogs), I get a dialog box like this:

[IMG]https://i.imgur.com/RMqPkDz.png[/IMG]

It populates the file name with "Documents".  Even removing that file name and changing the filter to "All files" will not show any files.

Firefox, which does not use the DE's file dialogs, continues to work fine.

I took a quick look through the KDE Bug List... but I haven't seen anyone else report it yet.  I was just wondering if it's only me before I dig further into and report it.

---

### Post by Ganton on 2024-03-08
> **3vi1 said:**
> Anyone else have an issue with the Open File dialog being broken?

If I go to any website, for instance imgur.com, and click the New Post "Upload File" button when using a chromium based browser (which uses the system/DE file dialogs), I get a dialog box like this:

[IMG]https://i.imgur.com/RMqPkDz.png[/IMG]

It populates the file name with "Documents".  Even removing that file name and changing the filter to "All files" will not show any files.

Firefox, which does not use the DE's file dialogs, continues to work fine.

I took a quick look through the KDE Bug List... but I haven't seen anyone else report it yet.  I was just wondering if it's only me before I dig further into and report it.

It doesn't happen to me when uploading an image to images.google.com (neither using Chromium or Firefox).

---

### Post by 3vi1 on 2024-03-08
> It doesn't happen to me when uploading an image to images.google.com (neither using Chromium or Firefox).

Hmmm... I'll need to investigate it more as a system-specific issue then.  Thank you for testing from your system; that tracks with the fact that there's no high priority matching bug on the KDE Bug list.

Thanks again!

---

### Post by Ganton on 2024-03-13
> **mahmoud-bahaa said:**
> Nop no ppa of sort yet and it won't even ship with ubuntu 24.04 but I am in progress of builting it on (k)ubuntu 24.04 and this the progress so far:


[*]Qt6 is outdated in ubuntu 24.04 (it has 6.4 while you need 6.5+) The best/easiest option is to either :

[*]- The easy way: Use qt-online-installer and download/install ONLY qt 6.6 binaries (no need for any other component)  [https://download.qt.io/official_releases/qt/6.6/6.6.2/single/](https://download.qt.io/official_releases/qt/6.6/6.6.2/single/)

[*]- The hard way: built it from source: [https://doc.qt.io/qt-6/linux-building.html](https://doc.qt.io/qt-6/linux-building.html) (had some issue with it so gave up on that)


This was the easier way for me: Using kde-builder to build Qt 6, and later Plasma 6 ([https://community.kde.org/Get_Involved/development/More#Build_Qt_using_kdesrc-build](https://community.kde.org/Get_Involved/development/More#Build_Qt_using_kdesrc-build)).

---

### Post by 3vi1 on 2024-03-31
My file-open issue went away at some point during one rebuild or another of workspace.  At this point, Plasma6.1 Dev seems as completely functional and stable as Plasma5 on my system; it's great!

I did find one more issue/fix I thought I'd post here to help anyone else that might be going down the same road:

I noticed that clicking links in my web browser (Vivaldi) which should have launched external apps, was not working.  Investigation showed xdg-open itself wasn't working.  Looking into that script, I found it has specific entries for KDE 5 and older.  So, you need to add logic to handle version 6:

```
open_kde()
{
    if [ -n "${KDE_SESSION_VERSION}" ]; then
      case "${KDE_SESSION_VERSION}" in
        4)
          kde-open "$1"
        ;;
        5)
          kde-open${KDE_SESSION_VERSION} "$1"
        ;;
       [B] 6)
          kde-open "$1"
        ;;[/B]
      esac
    else
        kfmclient exec "$1"
        kfmclient_fix_exit_code $?
    fi

    if [ $? -eq 0 ]; then
        exit_success
    else
        exit_failure_operation_failed
    fi
}

```

After that, lauching external apps from links in the browser works fine.

---

