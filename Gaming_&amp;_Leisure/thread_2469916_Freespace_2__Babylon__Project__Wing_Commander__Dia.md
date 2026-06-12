---
title: "Freespace 2 / Babylon  Project / Wing Commander / Diaspora natively under Ubuntu"
date: 2021-12-13
forum: Gaming &amp; Leisure
---

### Post by praseodym on 2021-12-13
Hi all,

the games mentioned above can now be easily installed natively without challenges via the Knossos combined installer/launcher:

Under 20.04:

```
sudo apt-get install git python3 build-essential libasyncns0:i386 libavahi-client-dev:i386 libc6:i386 libcaca0:i386 libdbus-1-3:i386 libflac8:i386 libgcc1:i386 libglu1-mesa:i386 libjansson4:i386 libjpeg-turbo8:i386 liblua5.1-0:i386 libncursesw5:i386 libogg0:i386 libopenal1:i386 libpulse0:i386 libpulse-dev:i386 libsdl1.2debian:i386 libsdl1.2-dev:i386 libslang2:i386 libsndfile1:i386 libstdc++6:i386 libtheora0:i386 libtinfo5:i386 libvorbis0a:i386 libvorbisenc2:i386 libvorbisfile3:i386 libwrap0:i386 libx11-6:i386 libxau6:i386 libxcb1:i386 libxdmcp6:i386 libxext6:i386 zlib1g:i386 python3-wheel python3-setuptools pyqt5-dev pyqt5-dev-tools qttools5-dev-tools qt5-default curl python3-pyqt5.qtwebengine python3-pyqt5.qtwebchannel python3-requests-toolbelt python3-ply git p7zip-full libopenal-dev ninja-build pipenv yarnpkg python3-semantic-version libsdl2-dev libgtk-3-dev liblzma-dev libzstd-dev zlib1g-dev 
sudo add-apt-repository ppa:linuxuprising/libpng12
sudo apt update
sudo apt-get install libpng12-0 
git clone https://github.com/ngld/old-knossos.git
cd old-knossos
pip3 install raven
pip3 install token-bucket
yarnpkg install
python3 configure.py
ninja run 
```

The total conversions Babylon Project, Diaspora, Wing Commander can be directly downloaded and played. For FS 2 you (still) need the installer purchased, e.g. from GOG [https://www.gog.com/game/freespace_2](https://www.gog.com/game/freespace_2)

[https://www.hard-light.net/forums/index.php?topic=94068.0](https://www.hard-light.net/forums/index.php?topic=94068.0)

[https://github.com/ngld/old-knossos](https://github.com/ngld/old-knossos)

---

