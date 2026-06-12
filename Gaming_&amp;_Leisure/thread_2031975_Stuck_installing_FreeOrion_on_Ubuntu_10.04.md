---
title: "Stuck installing FreeOrion on Ubuntu 10.04"
date: 2012-07-22
forum: Gaming &amp; Leisure
---

### Post by grandsatrap on 2012-07-22
This is what I get:

```
/home/griffin/games/FreeOrion>cmake .
-- Build platform: linux
-- Configuring freeoriond
-- Configuring freeorionca
-- Could NOT find Boost
CMake Error at client/AI/CMakeLists.txt:30 (message):
  Boost libraries not found.


-- Configuring incomplete, errors occurred!
```

These are the steps that I did:

```
#Follow instructions from this page: http://www.freeorion.org/index.php/Compile#Getting_the_source

sudo apt-get install build-essential subversion pkg-config libltdl3-dev cmake
sudo apt-get install python2.6-dev libfreetype6-dev libsdl1.2-dev libalut-dev libvorbis-dev libois-dev libtiff4-dev libopenal-dev libogre-dev
svn co https://freeorion.svn.sourceforge.net/svnroot/freeorion/trunk freeorion

#try to install Boost
sudo apt-get install libboost-dev  --install-recommends

#Still need to get boost!
#download it:
http://downloads.sourceforge.net/project/boost/boost/1.47.0/boost_1_47_0.tar.gz?r=http%3A%2F%2Fsourceforge.net%2Fprojects%2Fboost%2Ffiles%2Fboost%2F1.47.0%2F&ts=1343000189&use_mirror=superb-sea2

#extract the tar.gz file with its directory structure (done using Archive manager GUI), then
cd /home/griffin/Downloads/boost_1_47_0/libs/regex/build

make -fgcc.mak
#should it be SUDO ??

#copy all of /home/griffin/Downloads/boost_1_47_0/libs/regex/build/gcc to /usr/local/lib/boost_1_47
sudo cp -a * /usr/local/lib/boost_1_47/
# well, it looks like this didn't exactly work.

./bootstrap.sh
./b2
#this (./b2) takes a LOOONG time.

sudo ./bjam install

#*** BOOST is now installed and FreeOrion/cmake . can find it!

#install GIGI
cd GG
cmake -DBUILD_TUTORIALS=off -DBUILD_OGRE_DRIVER=ON -DBUILD_OGRE_OIS_PLUGIN=ON .
make

#sudo may not be necessary for these two lines
sudo make install
sudo ldconfig
#add in "/usr/local/lib" to sudo vi /etc/ld.so.conf  I assume that it just gets appended to the end.
#maybe rerun sudo ldconfig

#rerun cmake .
cmake .

#DAMN! Now it can't find Boost again!

```

---

