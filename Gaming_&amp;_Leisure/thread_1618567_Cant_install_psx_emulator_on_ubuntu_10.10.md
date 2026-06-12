---
title: "Cant install psx emulator on ubuntu 10.10"
date: 2010-11-10
forum: Gaming &amp; Leisure
---

### Post by luis_q88 on 2010-11-10
hello everyone, this is my very first post, i actually installed ubuntu 10.10 for the first time yesterday so i'm as noob as can be. i've been testing it out to see if i want to permanently switch to ubuntu from windows. and so far the only thing that has my banging my head on the keyboard is that i cant install epsxe (and other emulators but i'm focusing on this one for now) ive searched to forums and tried every suggestion and walkthrough but i find most of them are from like 2005 and 2007 and they dont work and as far as i know 10.10 is really recent. 

i'll tell you what ive tried:
[http://ubuntuforums.org/showthread.php?t=95835](http://ubuntuforums.org/showthread.php?t=95835)
then i tried
[http://ubuntuforums.org/showthread.php?t=95835](http://ubuntuforums.org/showthread.php?t=95835)

and hit a dead end when i finish the install and try to run epsxe from the Terminal i get:
luis@luis:~$ epsxe
./epsxe: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

and ive looked up this error and found a thread where it solved the problem for someone but i tried the same thing and didnt work for me, it keeps coming back saying
E: Unable to locate package libgtk1.2
E: Couldn't find any package by regex 'libgtk1.2'

and i cant run my friggin epsxe! also i know there are other psx emulators out there but ive always used epsxe and loved it, but if you can suggest a better one that will make my pain go away then by all means.
i need help bad, ive been reading about this for hours and i come up with old threads and broken links so please help me do this, this is a make or break thing for trying out ubuntu, if it wont do all the things i had windows doing then i'll get rid of but i really like it and wanna give a chance so i'm asking for help.
please show me a step by step thing on how to get this to work, i have 32 bit and again its 10.10

ps, i did the other things that were on the other posts and seems like its just gonna get discarded so have i done any damage at all by writting up these useless things on the Terminal??

thanks for the help and remember.. the future of my OS of choice rests in your [-o<hands

---

### Post by mister_playboy on 2010-11-11
Welcome to the forum... you've chosen a first task that is a bit hard for a beginner. ;)

[http://pcsxr.codeplex.com/releases/50048/download/140521](http://pcsxr.codeplex.com/releases/50048/download/140521)

You need to compile this, but it's not too difficult.  Your rule of thumb when you are told to compile something is to navigate to the directory inside the archive and run```
./configure
make
sudo make install
```
This works for 85-90% of cases.

You'll need to install the build dependencies before you compile. I don't remember what those are off-hand, so maybe someone else can tell us. :popcorn:  I'm sure you'll need more help beyond my post but just relax and you'll get your answers.

---

### Post by wingnux on 2010-11-11
Get OCSX-Reloaded from here: [http://pcsxr.codeplex.com/releases/view/50048](http://pcsxr.codeplex.com/releases/view/50048)

Download the appropriate deb file (32 or 64bit), double click it to install and it's all done. You'll just have to configure the plugins and bios.

---

### Post by Admoroux on 2010-12-05
I did next steps:

EPSXE
[http://www.epsxe.com/download.php](http://www.epsxe.com/download.php)
Plugins
[http://www.ngemu.com/psx/epsxe.php?action=plugins](http://www.ngemu.com/psx/epsxe.php?action=plugins)

1.Download ePSXe for Linux from official webpage.
2.Create a folder to save ePSXe. I did it on /usr/local/games/epsxe:
```
user@ubuntu:~$ sudo mkdir /usr/local/games/epsxe
``` 3. To simplify rest of steps, define a variable with full path
```
user@ubuntu:~$ export EPSXE='/usr/local/games/epsxe'
``` 4. Now, extract all files from .zip you donwloaded before. I asume that you use /tmp to save all downloaded files:
```
user@ubuntu:~$ sudo unzip -d $EPSXE /tmp/epsxe160lin.zip
``` 5. Define rights:
```
user@ubuntu:~$ cd $EPSXE
user@ubuntu:~$ sudo chmod 777 cfg sstates snap memcards
user@ubuntu:~$ sudo touch memcards/epsxe000.mcr memcards/epsxe001.mcr .epsxerc
user@ubuntu:~$ sudo chmod 666 memcards/*
user@ubuntu:~$ sudo chmod 666 .epsxerc
``` 6. Extract BIOS .zip on "bios" folder:
```
user@ubuntu:~$ sudo unzip -d $EPSXE/bios/ /tmp/SCPH1001.zip
``` 7. Extract right GPU Plug-in. I installed two of it. First, P.E.Op.S. Soft GPU in X version. This plugin is based on software, so it must run in all PC even you don't have 3D accelerator or if it isn't available on your X. The other one is Pete's MesaGL Linux PSX GPU witch is nice on 3D acceleration:
```
user@ubuntu:~$ sudo tar xfz /tmp/gpupeopssoftx117.tar.gz  -C $EPSXE/plugins/
user@ubuntu:~$ sudo tar xvfz /tmp/gpupetemesagl176.tar.gz  -C $EPSXE/plugins/
```8. Now, move config tool to "cfg" ePSXe subfolder:
```
user@ubuntu:~$ sudo mv $EPSXE/plugins/cfgPeopsSoft $EPSXE/cfg/
user@ubuntu:~$ sudo mv $EPSXE/plugins/gpuPeopsSoftX.cfg $EPSXE/cfg/
user@ubuntu:~$ sudo chmod 666 $EPSXE/cfg/gpuPeopsSoftX.cfg
user@ubuntu:~$ sudo mv $EPSXE/plugins/cfgPeteMesaGL $EPSXE/cfg/
user@ubuntu:~$ sudo mv $EPSXE/plugins/gpuPeteMesaGL.cfg $EPSXE/cfg/
user@ubuntu:~$ sudo chmod 666 $EPSXE/cfg/gpuPeteMesaGL.cfg
```9. Extract SPU Plug-in for sound. I downloaded P.E.O.p.S. OSS PSX SPU:
```
user@ubuntu:~$ sudo tar xvfz /tmp/spupeopsoss108.tar.gz -C $EPSXE/plugins/
``` 10. Move config tool to "cfg" again:
```
user@ubuntu:~$ sudo mv $EPSXE/plugins/cfgPeopsOSS $EPSXE/cfg/
```11. ePSXe it's for i386 structure, so it will not run if we don't get right version of libgtk1.2 and libglib1.2 on our x64 linux. I solved this issue downloading libgtk1.2_1.2.10-18.1build2_i386.deb and libglib1.2ldbl_1.2.10-19build1_i386.deb. We just need libgtk-1.2.so.0 and libgtk-1.2.so.0.9.1 from libgtk1.2, and libglib-1.2.so.0 and libglib-1.2.so.0.0.10 from libglib1.2. So, let's extract on /usr/lib32:
```
user@ubuntu:~$ sudo dpkg -x libgtk1.2_1.2.10-18.1build2_i386.deb /tmp/libgtk1.2
user@ubuntu:~$ sudo dpkg -x libglib1.2ldbl_1.2.10-19build1_i386.deb /tmp/libglib1.2
user@ubuntu:~$ sudo cp /tmp/libgtk1.2/usr/lib/libgtk* /usr/lib32
user@ubuntu:~$ sudo cp /tmp/libgtk1.2/usr/lib/libglib* /usr/lib32

```12. Make a symbolic link to GPU and SPU plugins to get libspu.so and libgpu.so, that's waht ePSX needs to run.[INDENT] a. 3D Acceleration
[/INDENT]```
user@ubuntu:~$ cd $EPSXE/plugins/
user@ubuntu:~$ sudo ln -sf libgpuPeteMesaGL.so* libgpu.so
user@ubuntu:~$ sudo ln -sf libspuPeopsOSS.so* libspu.so
```[INDENT]b. Software Acceleration
[/INDENT]```
 user@ubuntu:~$ cd $EPSXE/plugins/
 user@ubuntu:~$ sudo ln -sf libgpuPeopsSoftX.so* libgpu.so
 user@ubuntu:~$ sudo ln -sf libspuPeopsOSS.so* libspu.so
```13.Download Padjoy plugin for linux and extract it for use a gamepad
```
user@ubuntu:~$ cd /tmp
user@ubuntu:~$ sudo tar xfz padJoy073.tgz
user@ubuntu:~$ sudo cp padJoy/bin/libpadJoy-0.8.so $EPSXE/plugins/
user@ubuntu:~$ sudo cp padJoy/bin/cfgPadJoy $EPSXE/cfg/
```14.And that's all, folks! Just run:
```
user@ubuntu:~$ cd $EPSXE/
user@ubuntu:~$ ./epsxe
```Notes: I used OSS plugin because it's easier to find. To get an ALSA plugin, you must download OSS source code and compile it to ALSA. Elsewhere, if you want to run with OSS Plugin in PulseAudio, just run it as:
```
user@ubuntu:~$ padsp ./epsxe
```It runs nice to me, full speed at 1680*1050 on a GF8600GT, nice sound. I hope it's usefull for all, and excuse me for my english. I'm spanish and i don't use english to much! ^^

---

### Post by thatguruguy on 2010-12-05
Installing the .deb for pcsx-r is a LOT easier than all of that.

---

### Post by luis_q88 on 2010-12-22
sorry for taking so long to reply but unfortunately i had to switch back to windows, i do want to give ubuntu a try cuz i really liked it, 
i got a worry before going back to it, when i was trying to compile the script to get epsxe to work and it failed to work, i wondered if those failed compiled scripts would eventually screw up something on my computer, and if so, is there a way to undo those scripts? or do am i wrong and dont really have anything to worry about?

---

### Post by myromance123 on 2010-12-22
To get a PSX emulator up and running on ubuntu easily would have to be via a .deb file or through playdeb.net


 When installing through a .deb file or playdeb.net, you can just open up the Ubuntu Software Center and uninstall them if it doesn't work.

[www.playdeb.net]("http://www.playdeb.net/updates/Ubuntu/10.10#how_to_install")

Follow the instructions. Basically just do number 1 only. If it doesn't work, thats what number 2 is for.

 Then follow this playdeb.net link to install pcsxr on your ubuntu system,
[playdeb pcsxr]("http://www.playdeb.net/install/pcsxr/2%3A1.9.92-1%7Egetdeb1")

 From the menu that pops up, just make sure the words "Ubuntu Software Center" are highlighted and then select ok. If it prompts for password, provide it and then let it install. After that you should be able to find it located under Applications -> Games if Im not mistaken.

Give it a go :)

---

### Post by lazypower on 2010-12-24
Great post myromance123. Thanks for the instructions. WOrked like a charm

---

