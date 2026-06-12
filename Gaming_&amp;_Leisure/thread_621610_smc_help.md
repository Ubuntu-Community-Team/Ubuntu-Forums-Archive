---
title: "smc help"
date: 2007-11-23
forum: Gaming &amp; Leisure
---

### Post by thousandpimps on 2007-11-23
ok i got the deb file from smc website called smc data and smc...then  when i opened smc it said error no dependency ...
so i went file > open and pointed out smc data and then i installed the file....
but there was no link under application > games...so i typed smc in the terminal and it told me to install it by apt get smc...even though i thought i just installed it...
so i went o synaptic and installed smc and i still dont have a link under games to smc..

so this is my problem now...i wen to the terminal and typed smc and it gave me this error:
biccoloso@biccoloso-desktop:~$ smc
CEGUI::Exception: DynamicModule::DynamicModule - Failed to load module 'libCEGUIDevILImageCodec.so': libCEGUIDevILImageCodec.so: cannot open shared object file: No such file or directory
CEGUI Exception occurred : DynamicModule::DynamicModule - Failed to load module 'libCEGUIDevILImageCodec.so': libCEGUIDevILImageCodec.so: cannot open shared obj


any suggestions

---

### Post by disturbedite on 2007-11-24
1.  uninstall them all
2.  grab the smc packages from getdeb.net.
3.  make sure you have the following packages installed:
*libboost-filesystem1.34.1, libc6 (>= 2.6-1), libcegui-mk2-1, libgcc1 (>= 1:4.2.1), libgl1-mesa-glx | libgl1, libglu1-mesa | libglu1, libsdl-image1.2 (>= 1.2.5), libsdl-mixer1.2 (>= 1.2.6), libsdl-ttf2.0-0, libsdl1.2debian (>= 1.2.10-1), libstdc++6 (>= 4.2.1), smc-data (= 1.2-1~getdeb1), libcegui-mk2-dev*
4.  install smc-data & smc.

---

### Post by Leslie Viljoen on 2007-12-01
I didn't need to reinstall anything - just set some symbolic links that seem to have been omitted from the latest libcegui-mk2-1 package:

sudo su
cd /usr/lib
ln -s libCEGUIDevILImageCodec.so.0 libCEGUIDevILImageCodec.so
ln -s libCEGUIFalagardWRBase.so.1 libCEGUIFalagardWRBase.so
ln -s libCEGUIXercesParser.so.0 libCEGUIXercesParser.so

Then it all worked fine.

---

