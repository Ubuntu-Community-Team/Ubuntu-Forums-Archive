---
title: "Rigs of Rods !"
date: 2008-01-28
forum: Gaming &amp; Leisure
---

### Post by MaximB on 2008-01-28
Rigs of Rods is an advanced Truck/car/plane/boat simulator for GNU/Linux, windows and Mac OS's.
Several days ago a new version has been released - 0.34 which features a lot more trucks cars planes and bouts
It is closed source because the creator  fears that a company like Microsoft with it's simulators will see the code and make something like it.

Website : [http://rigsofrods.blogspot.com](http://rigsofrods.blogspot.com)
Download : [http://repository.rigsofrods.com/files/119/](http://repository.rigsofrods.com/files/119/)
If you have problems with libraries and dependencies : [http://forum.rigsofrods.com/index.php?topic=6331.0](http://forum.rigsofrods.com/index.php?topic=6331.0)
Loads of youtube videos : [http://www.youtube.com/results?search_query=rigs+of+rods&search_sort=video_date_uploaded](http://www.youtube.com/results?search_query=rigs+of+rods&search_sort=video_date_uploaded)

Soon a .deb package will arrive.

---

### Post by pibb69173 on 2008-01-28
hi, i need your help i get every thing running the game window comes up for about a sec then i get a error 

error: unsupported depth 0... exiting

im at a loss and not sure what do plz help

p.s. i got the setting window to run

---

### Post by MaximB on 2008-01-29
I have searched their forums but found no answer.
Try asking them in their forum : [http://forum.rigsofrods.com](http://forum.rigsofrods.com)

---

### Post by SOULRiDER on 2008-01-29
Im not into simulators of this kind, but it does look good to me, maybe ill give it a try.

---

### Post by pibb69173 on 2008-01-29
> **MaximB said:**
> I have searched their forums but found no answer.
Try asking them in their forum : [http://forum.rigsofrods.com](http://forum.rigsofrods.com)

thanx i just posted

---

### Post by kr00lplatinum on 2008-01-29
Would you be kind enough too post the directions on how a n00b would install this game under Ubuntu 7.10? 

Thanks for your help!

---

### Post by Perfect Storm on 2008-01-29
Extract it

cd /into/the/folder
./RoR


If it complains about some libs, you need to install them via synaptic.

---

### Post by kr00lplatinum on 2008-01-29
Sorry, That doesn't really help a total n00b. 

Could you post step by step what I'm supposed to do in the Terminal? 

That would be most beneficial to me.

---

### Post by Perfect Storm on 2008-01-29
```
cd Desktop
tar jxfv RoR-linux-0.34.tar.bz2
cd RoR-linux-0.34
./RoR
```

---

### Post by Steveway on 2008-01-29
> It is closed source because the creator fears that a company like Microsoft with it's simulators will see the code and make something like it.

Ok, that is just plain stupid. A proper Open-source license prevents this.
The true reason is: They want to either infect you with Spyware, viruses, rootkits and such stuff or they want to make all versions disfunction in the future and from then people will have to pay for it.
So called Freeware is only a trick to damage you, if they really want to give it away for free then they can easily open the source.

---

### Post by Perfect Storm on 2008-01-29
Well it gives us 64-bit users a headache to get to work as it made for 32-bit :(
Some of the dependenies of rods of rigs is abnormal (ex. a special ogre plugin is needed to make the game work that means you need to compile ogre for 32-bit on your 64-bit and enable the plugin).
Plus you have to make alot of symblink in your /usr/lib32 for libs you have installed via getlibs because it uses diffrent names for the same libs.

---

### Post by MaximB on 2008-01-29
> **Artificial Intelligence said:**
> ```
cd Desktop
tar jxfv RoR-linux-0.34.tar.bz2
cd RoR-linux-0.34
./RoR
```

Before running the game do :

```
sudo apt-get install libdevil1c2 libopenal0a libgl1-mesa-glx libfreetype6 libtiff4 nvidia-cg-toolkit
```
This will install all dependencies.

Notes:
Because Thomas compiles on Gentoo, our libraries may differ.  you have to symlink libtiff.so.3->current libtiff and libopenal.so.1->current libopenal.

You can also locate the files libtiff.so and libopenal.so , copy them to the game directory and rename them to :
libtiff.so.3 and libopenal.so.1 accordingly.

Steveway :
It's their game, and their decision.
Play it or leave it.

---

### Post by ericsp on 2008-02-02
Folowed the above protocol and get the following response:

```
./RoR.bin: error while loading shared libraries: libzzip-0.so.13: cannot open shared object file: No such file or directory

```

HELP!

---

### Post by Perfect Storm on 2008-02-02
```
sudo aptitude install libzzip-0-13
```

If it doesn't help

then;
```
sudo ln -s /usr/lib/libzzip-0.so.13.0.49 /usr/lib/libzzip-0.so.13
```

---

### Post by Christopherius on 2008-03-09
> **Artificial Intelligence said:**
> ```
sudo aptitude install libzzip-0-13
```

If it doesn't help

then;
```
sudo ln -s /usr/lib/libzzip-0.so.13.0.49 /usr/lib/libzzip-0.so.13
```

i tried the code and got the following message in my terminal:

```
chris@chris-desktop:~$ sudo aptitude install libzzip-0-13Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No candidate version found for libzzip-0-13
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
chris@chris-desktop:~$ 

```

---

### Post by Perfect Storm on 2008-03-10
You need to Gutsy to do it. Or you have to compile it that lib (as I can see you use Feisty).

---

### Post by Bionic Apple on 2008-03-13
Hmmm... I feel like an idiot, but I need help.  When I add the Ubuntu/Debian package link to my repository sources list, the package manager totally rejects it.  It needs a "gutsy main universe" or something like that after link.  However, I don't know if there is another way or if I need to use specific keywords.

**Nevermind**, apparently that extra forward slash was needed.  I feel like an idiot yet again.

By the way, the .deb packages apparently don't work immediately.  I am going to see if I have to make those symlinks.

---

### Post by k33bz on 2008-03-14
ok, I am giving a crack at this game as well.  Using Fiesty, getting the same feed back when i try to sudo aptitude libzzip-0-13.  Looked around on the net, cant find a deb installer for that library as of yet. but have found an rpm of it though, so I am going to try to go that route.

[http://rpmfind.net/linux/rpm2html/search.php?query=libzzip-0.so.13]("http://rpmfind.net/linux/rpm2html/search.php?query=libzzip-0.so.13")

just noticed the name difference, libzzip-0.so.13, hope that dont make any difference.

---

### Post by k33bz on 2008-03-14
well, downloaded that library as an RPM file, converted it to a DEB file, seemed so far so good.   BUT, of course no go, lol, totally different name, not LIBZZIP-0-13 but it is ZZIPLIB-0.13.etc etc etc................

oh well, I will look around, unless some one can tell me how i can make that work.


ok, I found the right library, here is the link for those who want to know, just having a little trouble myslef, dont want to recognize libc6.
[http://packages.debian.org/sid/i386/libzzip-0-13/download]("http://packages.debian.org/sid/i386/libzzip-0-13/download")

---

### Post by MaximB on 2008-04-15
A new version has came out 0.35 and now with Debian/Ubuntu new bright .deb package !!!
Get it here : [http://wiki.rigsofrods.com/index.php?title=Installation_Guide#Ubuntu.2FDebian](http://wiki.rigsofrods.com/index.php?title=Installation_Guide#Ubuntu.2FDebian)
For other versions : [http://repository.rigsofrods.com/](http://repository.rigsofrods.com/)

---

### Post by MaximB on 2009-02-16
Good News 
RoR is going to be open source under the GPLv3 soon !

From the blog :

"I decided to publish the source code of Rigs of Rods 0.36 under the GPLv3 licence.
Why this decision?

    * To attract and motivate more volunteers and contributors.
    * To give us some oxygen. The project is too big to maintain for just Thomas and me. Also, we have the desire to turn the page and work on new projects, possibly related to RoR, but I don't want to "kill" RoR by doing so.
    * To give back to all the Open Source projects that gave us the possibility to use their code under the LGPL, like Ogre3D.
    * To be able to use the resources offered by SourceForge for Open Source projects.
    * To ease the porting of RoR to the Linux platform.

This will have no influences on the release of 0.36, which is close to be finished (the code is finished, and we are selecting and testing the contents. Unfortunately my computer decided this was the right time to have a hardware malfunction, and I'm finishing with half my RAM!).

There will be a more formal Open Source announcement to build the hype once 0.36 is released."

[http://rigsofrods.blogspot.com/](http://rigsofrods.blogspot.com/)

You can replay and speak about it in their official forums here :
[http://forum.rigsofrods.com/index.php?topic=17997.msg153692#msg1536](http://forum.rigsofrods.com/index.php?topic=17997.msg153692#msg1536)

BTW The 0.36 release is on it's way !

---

### Post by Sealbhach on 2009-10-15
I still can't build it, tried in 8.10, 9.04 and now 9.10. It never works for me...

.

---

### Post by Perfect Storm on 2009-10-16
> **Sealbhach said:**
> I still can't build it, tried in 8.10, 9.04 and now 9.10. It never works for me...

.

It have changed a lot how to build.

[http://gwos.org/doku.php/guides:64bit:rigs_of_rods](http://gwos.org/doku.php/guides:64bit:rigs_of_rods)

---

### Post by TobiasV on 2009-10-16
I just followed your guide, and got stuck at the

./rorconfig.shpart, it says: 

[EMAIL="tobias@tobias-desktop:%7E/.Games"]tobias@tobias-desktop:~/.Games[/EMAIL]/RoR/test/current$ ./rorconfig.sh
./rorconfig.sh: line 4: ./rorconfig: No such file or directory

I looked at the file, but I know squat, so I couldn't figure out what was wrong...

Also: Earlier you mention that you have to remove a particular line from the
plugins.cfgfile, but that line is already commented out, does it still need to me removed (I did so)?

-Tobias

Edit: Here's the content of rorconfig.sh:

> #!/bin/bash
BASEDIR=${0%/*}
export LD_LIBRARY_PATH="$LD_LIBRARY_PATH:$BASEDIR/"
$BASEDIR/rorconfig $@

# this should fix the hanging keys problem
if [[ "$(which xset)" != "" ]]
then
 xset r on
else
 echo "please install 'xset' in order to fix the key repeat bug that occurs som$
fi



---

### Post by Perfect Storm on 2009-10-16
> **TobiasV said:**
> I just followed your guide, and got stuck at the

./rorconfig.shpart, it says: 

[EMAIL="tobias@tobias-desktop:%7E/.Games"]tobias@tobias-desktop:~/.Games[/EMAIL]/RoR/test/current$ ./rorconfig.sh
./rorconfig.sh: line 4: ./rorconfig: No such file or directory

I looked at the file, but I know squat, so I couldn't figure out what was wrong...

Also: Earlier you mention that you have to remove a particular line from the
plugins.cfgfile, but that line is already commented out, does it still need to me removed (I did so)?

-Tobias

Edit: Here's the content of rorconfig.sh:

I'll take a look at it again, they might have changed it again *sigh*

If it commented out, no need to remove it.

---

### Post by Sealbhach on 2009-10-16
> **Artificial Intelligence said:**
> It have changed a lot how to build.

[http://gwos.org/doku.php/guides:64bit:rigs_of_rods](http://gwos.org/doku.php/guides:64bit:rigs_of_rods)

Oh hey, I got it up and running using the method you linked to. I had tried the method on their website: [http://wiki.rigsofrods.com/pages/Compiling_Sources](http://wiki.rigsofrods.com/pages/Compiling_Sources)

Which doesn't seem to work. I've just had a brief look at it, and there's no sound so far, but at least it compiles anyway.:)

Thanks for your help.

.

---

### Post by Aperion on 2010-01-05
Thought I'd chime in, I'm one of the Devs for RoR, and I've LOVE to get it more popular for linux and Ubuntu in general. I'd also love to pick up a package maintainer for Ubuntu. If you have questions, or need help let me know, I will stay subscribed to this thread. so I'll notifications.

I must say that the build System currently used if fubared I do not use it at all, just FYI. 

Actually is someone wants to work with me I can provide binaries to build packages for 64bit 9.10, and maybe other if I'm motivated to setup the proper VMs.

---

### Post by MaximB on 2010-01-05
Hello Aperion !

I'm not a package builder or maintainer but I think for start you (or someone else) needs to build the first packages (32 and 64) , when a package is at hand - more people will come and the game will be more popular.

Also consider making a universal package to suite all distros, so les maintainers will be needed.

---

### Post by Aperion on 2010-01-05
> **MaximB said:**
> Hello Aperion !

I'm not a package builder or maintainer but I think for start you (or someone else) needs to build the first packages (32 and 64) , when a package is at hand - more people will come and the game will be more popular.

Also consider making a universal package to suite all distros, so les maintainers will be needed.

Actually there were some packages once upon a time, but that was before it went open source. Pert of the difficulty is that RoR has been previously developed in a windows environment, so it builds all of it's libraries and packages them together. And then it is released as excepted to be all run from the same directory. Not being package person I'm not really sure what should go where.

---

### Post by Fred the Penguin on 2010-02-13
I have added Rigs of Rods 0.34 to the repositories, but when I try to download it it comes up with this:  Depends: libopenal0a (>=0.0.8 but it is not installable.  That is the only dependency I still need.  Symbolic links did not do anything, but I might have been doing them to the wrong things.  The libopenals i have are:   
/home/jonathan/libopenal.so.1
/usr/lib/libopenal.so.1
/usr/lib/libopenal.so.1.8.466
/usr/lib/debug/usr/lib/libopenal.so.1.8.466
 and i seem to have libopenal0a.  I was following the directions at [http://wiki.rigsofrods.com/pages/Installation_Guide#Ubuntu.2FDebian](http://wiki.rigsofrods.com/pages/Installation_Guide#Ubuntu.2FDebian)

I tried following the link that artificial intelligence had, but when i try to run it I get this:sh: ./RoR.sh: Permission denied

---

### Post by k8962c on 2010-02-24
Hi all, first post on here i think!
I've been messing around with Rigs of Rods recently and loving it, currently using the debs for v0.34 as I can't get v0.36 working.

> **Fred the Penguin said:**
> I have added Rigs of Rods 0.34 to the repositories, but when I try to download it it comes up with this:  Depends: libopenal0a (>=0.0.8 but it is not installable.  That is the only dependency I still need.
I had the same problem and I think i fixed it by adding one of the older repositories [like ibex or jaunty or something] which had the exact same lib, it doesn't seem to be present in the karmic repos.


Now however I'm trying to get v0.36 working for the more uptodate planes/addons etc. I got the source and data from sourceforge for v0.36.3

It seems to do "make" perfectly well, but has problems when trying to run it [mainly files/libs in the wrong places I think, even though they seem to be present and correct!]
Also the rorconfig always throws a segfault when I try to save the configuration.

Has anyone else got any tips on build configuration or errors with rorconfig?
You (Aperion) said about how the build system is fubared, what method do you currently use to build it; if i can try to replicate your method I might have better luck!!

Thanks for any/all help you can give,
EJ  [Ubuntu 9.10]

---

### Post by ra3don on 2010-02-24
Rigs of Rods is awesome, however back when I used to play it, it was disappointing to see that I couldn't get the latest version in the repository. I think it could definently gain some momentum in the linux world now that it is open source.

---

### Post by Fred the Penguin on 2010-02-28
Thank you. I added ubuntu hardy's repositories to install libopenal0a and RoR 0.34 worked.  I have tried to follow the instructions that artificial intelligenge posted but I was denied permission when I tried to open it.  I downloaded the :( Windows:(  release 0.36.3 or 0.37 beta (I'm not sure which) and it worked on wine, though when I tried to add vehicles, it took some others away.

---

### Post by Fred the Penguin on 2010-03-22
Sometimes, rigs of rods crashes when I try to use certain vehicles. This is one of very few things that works better on Windows.

---

### Post by Aperion on 2010-04-02
I'll see what I can do once I get RoR up and running again. perhaps I'll surprise the community with some packages.

---

### Post by zzarko on 2010-04-15
I tried to compile 0.36.3 on Ubuntu 9.10 32-bit. Compilation went all well, but I was unable to successfully start rorconfig.sh. After running it, it's window flashes for a moment and this is what I get from terminal (among other text with stuff that went well):
```
...
asking system for default language.
 system returned: English (U.S.) (en_US)
preferred language: English (U.S.)
lang file: /media/Download/RigsOfRods/0.36.3/test/current/languages/en/ror.mo
language existing, using it!
getOISHandle(): Window needs to be realized before we can get its XID. Showing the window to avoid crash!

(rorconfig:378): Gtk-CRITICAL **: gtk_window_resize: assertion `width > 0' failed
reading from Config file: /home/zzarko/RigsOfRods/config/RoR.cfg
>> If it crashes after here, check your plugins.cfg and remove the DirectX entry if under linux!
Creating resource group General
Creating resource group Internal
Creating resource group Autodetect
...
```There is an assertion `width > 0' failed and I guess this is the reason I didn't get window to show properly. If I try to run the game anyway (RoR.sh), I get this output:
```
...
Loading library ./Plugin_CgProgramManager

An exception has occured!: OGRE EXCEPTION(7:InternalErrorException): Could not load dynamic library ./Plugin_CgProgramManager.  System Error: ./Plugin_CgProgramManager.so: cannot open shared object file: No such file or directory in DynLib::load at /media/Download/RigsOfRods/0.36.3/build/dependencies/ogre/OgreMain/src/OgreDynLib.cpp (line 81) / url: http://wiki.rigsofrods.com/index.php?title=Error_7#DynLib::load
```Line with DirectX is commented-out in plugins.cfg. This is as fas as I could get. Any advices what to try next?

Best regards,
Zarko

---

### Post by Aperion on 2010-04-15
> **zzarko said:**
> I tried to compile 0.36.3 on Ubuntu 9.10 32-bit. Compilation went all well, but I was unable to successfully start rorconfig.sh. After running it, it's window flashes for a moment and this is what I get from terminal (among other text with stuff that went well):
```
...
asking system for default language.
 system returned: English (U.S.) (en_US)
preferred language: English (U.S.)
lang file: /media/Download/RigsOfRods/0.36.3/test/current/languages/en/ror.mo
language existing, using it!
getOISHandle(): Window needs to be realized before we can get its XID. Showing the window to avoid crash!

(rorconfig:378): Gtk-CRITICAL **: gtk_window_resize: assertion `width > 0' failed
reading from Config file: /home/zzarko/RigsOfRods/config/RoR.cfg
>> If it crashes after here, check your plugins.cfg and remove the DirectX entry if under linux!
Creating resource group General
Creating resource group Internal
Creating resource group Autodetect
...
```There is an assertion `width > 0' failed and I guess this is the reason I didn't get window to show properly. If I try to run the game anyway (RoR.sh), I get this output:
```
...
Loading library ./Plugin_CgProgramManager

An exception has occured!: OGRE EXCEPTION(7:InternalErrorException): Could not load dynamic library ./Plugin_CgProgramManager.  System Error: ./Plugin_CgProgramManager.so: cannot open shared object file: No such file or directory in DynLib::load at /media/Download/RigsOfRods/0.36.3/build/dependencies/ogre/OgreMain/src/OgreDynLib.cpp (line 81) / url: http://wiki.rigsofrods.com/index.php?title=Error_7#DynLib::load
```Line with DirectX is commented-out in plugins.cfg. This is as fas as I could get. Any advices what to try next?

Best regards,
Zarko

hmm, do you have a ~/RigsOfRods directory? On first run of rorconfig it should setup that directory, if not then copy the skeleton folder from the RoR.sh directory to ~ and rename to RigsOfRods. then try running rorconfig again. I remember that running it for the first time was a major PITA. Thanks for reminding me of this, unfortunately once it's working right I have a tendency to forget about it.

---

### Post by zzarko on 2010-04-16
> **Aperion said:**
> hmm, do you have a ~/RigsOfRods directory? On first run of rorconfig it should setup that directory, if not then copy the skeleton folder from the RoR.sh directory to ~ and rename to RigsOfRods. then try running rorconfig again. I remember that running it for the first time was a major PITA. Thanks for reminding me of this, unfortunately once it's working right I have a tendency to forget about it.
I checked that, I have ~/RigsOfRods directory, but rorconfig.sh still gives assertion (but, after assertion, it gives a lot of output about registering various components). After rorconfig finishes, I have in ~/RigsOfRods/config directory various config files, but two of them, ogre.cfg and RoR.cfg, are empty. I have compiled RoR not in my home directory (I filled that up :( ), but on another partition, maybe that's the problem?
Also, OGRE error after starting RoR.sh suggests that I don't have DirectX. I checked again, plugins.cfg has DirectX line commented-out. If you have any idea where should I look, I'm familiar with debuggers, programming (C/C++/Python/bash/...), and I could try to find the problem (I just don't know where to start, code-base is HUGE :) ).

Edit:
I forgot to mention, I have libogre and libogre-dev installed on my system from before, version 1.6.1. Could that be a problem?

---

### Post by Aperion on 2010-04-16
> **zzarko said:**
> I checked that, I have ~/RigsOfRods directory, but rorconfig.sh still gives assertion (but, after assertion, it gives a lot of output about registering various components). After rorconfig finishes, I have in ~/RigsOfRods/config directory various config files, but two of them, ogre.cfg and RoR.cfg, are empty. I have compiled RoR not in my home directory (I filled that up :( ), but on another partition, maybe that's the problem?
Also, OGRE error after starting RoR.sh suggests that I don't have DirectX. I checked again, plugins.cfg has DirectX line commented-out. If you have any idea where should I look, I'm familiar with debuggers, programming (C/C++/Python/bash/...), and I could try to find the problem (I just don't know where to start, code-base is HUGE :) ).

Edit:
I forgot to mention, I have libogre and libogre-dev installed on my system from before, version 1.6.1. Could that be a problem?

This sounds extremely familiar. You might try uninstalling the system version of Ogre. RoR does compile supply it's own version of Ogre and all the libraries (a requirement for windows) the only problem I can imagine this causing is RoR loading up the system library then reading the plugins.cfg file and trying to load the supplied plugins, even then I'm not sure that would cause a problem.

---

### Post by jtbo on 2010-04-19
I made some testing and blogged while I installed RoR [http://forum.rigsofrods.com/index.php?topic=32273.0](http://forum.rigsofrods.com/index.php?topic=32273.0) I will do still some edits to it, but that should perhaps be helpful for newcomers? 

That is how I got it to work with Xubuntu 9.10 64-bit and RoR 0.36.3.

---

### Post by zzarko on 2010-04-20
> **jtbo said:**
> I made some testing and blogged...
I also had wxrc problem (I didn't paid attention to it until I saw your posts). In Ubuntu, it can be solved by installing wx-common package.
I'm trying to compile it again... I'll post if anything goes better than the first time.

Edit:
After compiling again (without errors; ogre libs removed from system) I still get
```
(rorconfig:30477): Gtk-CRITICAL **: gtk_window_resize: assertion `width > 0' failed
```when starting rorconfig.sh and I still get
 ```
An exception has occured!: OGRE EXCEPTION(7:InternalErrorException): Could not load dynamic library ./Plugin_CgProgramManager.  System Error: ./Plugin_CgProgramManager.so: cannot open shared object file: No such file or directory in DynLib::load at /media/Download/RigsOfRods/0.36.3/build/dependencies/ogre/OgreMain/src/OgreDynLib.cpp (line 81) / url: [http://wiki.rigsofrods.com/index.php?title=Error_7#DynLib::load](http://wiki.rigsofrods.com/index.php?title=Error_7#DynLib::load)
```although direct3d line is commented in plugins.cfg. Even tried to run it as root, same thing. So, I guess I'm stuck at the moment...

Edit2:
I just remembered, the first time I tried to compile RoR, I got error about three environment variables not defined (I don't remember which three, I remember that one of them had OGRE in its name). I installed libogre-dev from repository, and those errors were gone, but even after removing libogre-dev (complete remove + restart), I no longer have this error displayed. set | grep -i ogre also returns no variables with ogre in its name.

---

### Post by Aperion on 2010-04-20
Can you post your plugins.cfg file? and the location where the plugins are located.

---

### Post by zzarko on 2010-04-21
Everything is unpacked in /media/Download/RigsOfRods/0.36.3/. plugins.cfg is in /media/Download/RigsOfRods/0.36.3/test/current and its contet is:
-------------------
# Defines plugins to load

# Define plugin folder
PluginFolder=.

# Define plugins
#Plugin=RenderSystem_Direct3D9
Plugin=RenderSystem_GL
Plugin=Plugin_ParticleFX
Plugin=Plugin_OctreeSceneManager
Plugin=Plugin_CgProgramManager
-------------------
Plugins are in the same directory (RenderSystem_GL.so, Plugin_ParticleFX.so and Plugin_OctreeSceneManager.so; there is no Plugin_CgProgramManager nor RenderSystem_Direct3D9).

---

### Post by Aperion on 2010-04-21
> **zzarko said:**
> 
there is no Plugin_CgProgramManager nor RenderSystem_Direct3D9).ahha! that's the problem, not the D3D thing but the CgProgramManager
 you're using the 0.36.3 source? which means it should be compiling it, make sure you have the cg dev installed. You might have to download it from nvidias website.

---

### Post by zzarko on 2010-04-22
> **Aperion said:**
> ahha! that's the problem, not the D3D thing but the CgProgramManager
 you're using the 0.36.3 source? which means it should be compiling it, make sure you have the cg dev installed. You might have to download it from nvidias website.
That did the trick! It works!
Strangely, I didn't get any compiling errors about ProgramManager, or missing nvidia cg header files.

Thank you again! I'll try to repeat installation on vanilla-ubuntu and to write down all the steps to get working RoR...

---

### Post by Aperion on 2010-04-22
> **zzarko said:**
> That did the trick! It works!
Strangely, I didn't get any compiling errors about ProgramManager, or missing nvidia cg header files.

Thank you again! I'll try to repeat installation on vanilla-ubuntu and to write down all the steps to get working RoR...

You were working on 0.36.3? the SVN build system has greatly changed, all of the dependencies included previously have been removed.

I assume you've seen the docs here:
[http://wiki.rigsofrods.com/pages/Compiling_Sources_under_Ubuntu_Linux](http://wiki.rigsofrods.com/pages/Compiling_Sources_under_Ubuntu_Linux)

They are out of date, I think I'm basically the one trying to get the build system to work under Linux. What I need to do is write a bash script to assist with compiling all the needed libraries. With a longer term goal of putting up a repository.

---

### Post by jtbo on 2010-04-22
I made bit more progress again, but I made stupid error, I did install Ogre 1.8.0 from source when I was going to install 1.7.X, thing hit me after I had installed all.

Now as I have installed that from source, how do I uninstall it so that nothing breaks down? I will install 1.7.X from sources too as I can't get otherwise boost 1.42 installed, ogre installation installs boost 1.38 when using apt-get and I really would like to learn to do some stuff without apt-get :)

Btw editing that plugins.cfg is very important step, from wiki instruction page there would be perhaps good idea to remove part where moving lot of stuff is mentioned and replace that with information how to edit plugins.cfg?

---

### Post by Aperion on 2010-04-22
> **jtbo said:**
> I made bit more progress again, but I made stupid error, I did install Ogre 1.8.0 from source when I was going to install 1.7.X, thing hit me after I had installed all. I didn't even know they had 1.8 out :)

> **jtbo said:**
> 
Now as I have installed that from source, how do I uninstall it so that nothing breaks down? I will install 1.7.X from sources too as I can't get otherwise boost 1.42 installed, ogre installation installs boost 1.38 when using apt-get and I really would like to learn to do some stuff without apt-get :)

I think to remove it you have to manually remove the files, fortunately they should be contained in their own sub-directories.

I am using 9.10 and there are two versions of boost available, the older version should work correctly.

> **jtbo said:**
> 
Btw editing that plugins.cfg is very important step, from wiki instruction page there would be perhaps good idea to remove part where moving lot of stuff is mentioned and replace that with information how to edit plugins.cfg?
yes editing the plugins.cfg is an important step, I hope to automate that through the build system though. if ogre was installed to /usr/local then the plugin directory needs to be changed from "." to "/usr/local/lib/OGRE" although there is hopefully a patch in Ogre that allows it to check the existing paths for the libraries.

Which part of the steps are you moving stuff around? I haven't read the readme in ages and it is probably extremely out of date.

Sorry all for the state of things, hopefully it will improve, and thanks putting up with it and pushing forward! I know how frustrating it can be.

---

### Post by jtbo on 2010-04-22
> **Aperion said:**
> 
Which part of the steps are you moving stuff around? I haven't read the readme in ages and it is probably extremely out of date.

Sorry all for the state of things, hopefully it will improve, and thanks putting up with it and pushing forward! I know how frustrating it can be.

I should of type that more clearly, I meant Wiki page of [http://wiki.rigsofrods.com/pages/Compiling_Sources_under_Ubuntu_Linux]("http://wiki.rigsofrods.com/pages/Compiling_Sources_under_Ubuntu_Linux") where it says:
> I eventually got it to work by moving the whole lot to /RigsOfRods. I must be missing something as this is an insane place to put it - but it looks like this location is hard-coded into the default build? So much doesn't work if RoR isn't there...

That lead me to experiment with copying stuff instead of editing plugins.cfg but there is no need to copy anything, just edit that file.

Currently I did mange to have situation where I do have two versions of Ogre installed, which may not be too good. However I'm not too familiar with directories of linux, I would guess that removing OGRE directories from /usr and subfolders would remove Ogre. 

Ogre 1.8.0 is unstable, there is no binaries for it yet, I did forget these from one command ```
-u v1-7
``` and that gave me 1.8.0, however I don't know if that would prevent RoR to run, at least with that RoR does not crash and I get black Ogre render window, hitting esc I see even ending credits, haven't got so far with 1.7.0 which complains from missing files even I edit plugins.cfg.

What is your opinion guys, does it cause problems when I have two Ogre versions? 

I'm enough stupid and stubborn to push trough solid rock, trying to figure out this is not so bad, just sometimes it takes few hours to download stuff because of my slow connection, but there I can kill time with 0.36.3 version of RoR :P

---

### Post by Aperion on 2010-04-23
> **jtbo said:**
> I should of type that more clearly, I meant Wiki page of [http://wiki.rigsofrods.com/pages/Compiling_Sources_under_Ubuntu_Linux]("http://wiki.rigsofrods.com/pages/Compiling_Sources_under_Ubuntu_Linux") where it says:


That lead me to experiment with copying stuff instead of editing plugins.cfg but there is no need to copy anything, just edit that file.

Currently I did mange to have situation where I do have two versions of Ogre installed, which may not be too good. However I'm not too familiar with directories of linux, I would guess that removing OGRE directories from /usr and subfolders would remove Ogre. 

Ogre 1.8.0 is unstable, there is no binaries for it yet, I did forget these from one command ```
-u v1-7
``` and that gave me 1.8.0, however I don't know if that would prevent RoR to run, at least with that RoR does not crash and I get black Ogre render window, hitting esc I see even ending credits, haven't got so far with 1.7.0 which complains from missing files even I edit plugins.cfg.

What is your opinion guys, does it cause problems when I have two Ogre versions? 

I'm enough stupid and stubborn to push trough solid rock, trying to figure out this is not so bad, just sometimes it takes few hours to download stuff because of my slow connection, but there I can kill time with 0.36.3 version of RoR :P
having two version of any library has potential problems, I think linking RoR to Ogre should link against a specific verison, but I'm not completely sure how to tell the linker that...

to see which ogre version it's linking against use  ldd `pwd`/RoR

I totally forgot about the little tutorial I wrote on compiling the dependencies, see here: [http://wiki.rigsofrods.com/pages/Compiling_without_the_supplied_3rd_party_libraries](http://wiki.rigsofrods.com/pages/Compiling_without_the_supplied_3rd_party_libraries)

---

### Post by jtbo on 2010-04-23
> **Aperion said:**
> having two version of any library has potential problems, I think linking RoR to Ogre should link against a specific verison, but I'm not completely sure how to tell the linker that...

to see which ogre version it's linking against use  ldd `pwd`/RoR

I totally forgot about the little tutorial I wrote on compiling the dependencies, see here: [http://wiki.rigsofrods.com/pages/Compiling_without_the_supplied_3rd_party_libraries](http://wiki.rigsofrods.com/pages/Compiling_without_the_supplied_3rd_party_libraries)

That linky is good, thx. 

I started working with all those systematically to verify that I don't miss anything, some of those I should already have installed. 

With Mygui I run into odd problem, after make command (without silent) it did run into slight problem, I believe. Computer that is compiling has been at 70% for few hours now, even mouse pointer is not moving anymore and ctrl+c seem not to help, looks like I got whole system to freeze up, it does not respond even to ping, I thought it would be impossible with linux for single program to cause whole system to lock up? :)

Other than that, I got 1.8.0 Ogre removed, also 1.7.0 and found out that 1.7.0 from Ogre PPA is lacking a bit, there were at least one .so file that was not there, but one compiled from source had it, so at least for me that binary version did not work, but source version does work. I have kind of working RoR, according to tdev it is just missing mygui so no menus, but with commands revealed from ror --help I have not been able to get it to run yet and compiling with mygui enabled gives lot of errors, so I try to install new mygui from source and maybe it will work with gui or then not, anyway more testing == more experience. I put more into thread in RoR forums when I test things, I put url here again [http://forum.rigsofrods.com/index.php?topic=32273.0](http://forum.rigsofrods.com/index.php?topic=32273.0)

---

### Post by Aperion on 2010-04-23
> **jtbo said:**
> With Mygui I run into odd problem, after make command (without silent) it did run into slight problem, I believe. Computer that is compiling has been at 70% for few hours now, even mouse pointer is not moving anymore and ctrl+c seem not to help, looks like I got whole system to freeze up, it does not respond even to ping, I thought it would be impossible with linux for single program to cause whole system to lock up? :)

That's odd behavior. although I have seen make almost lock up my system before. it was a problem of not enough ram, I had I was running 64 bit with 8 jobs (-j8) since I have a quad core and only 2 GB of RAM, I needed 4 more to make it happy.

What file system are you running? if you're running XFS it might need de-fragmenting. Those are the only things I've seen cause my linux system to freeze up, otherwise just random glitches. In which case trying again would work properly.

---

### Post by nikhilbhardwaj on 2010-04-23
> **Steveway said:**
>  The true reason is: They want to either infect you with Spyware, viruses, rootkits and such stuff or they want to make all versions disfunction in the future and from then people will have to pay for it.
So called Freeware is only a trick to damage you, if they really want to give it away for free then they can easily open the source.  get a life

---

### Post by jtbo on 2010-04-23
> **Aperion said:**
> That's odd behavior. although I have seen make almost lock up my system before. it was a problem of not enough ram, I had I was running 64 bit with 8 jobs (-j8) since I have a quad core and only 2 GB of RAM, I needed 4 more to make it happy.

What file system are you running? if you're running XFS it might need de-fragmenting. Those are the only things I've seen cause my linux system to freeze up, otherwise just random glitches. In which case trying again would work properly.

Probably it did run out of ram, I'm still having issue with that machine's swap file, it is dual boot and I made error when partitioning so my swap file space is unusable piece of disk at the moment (location of free space not allowing creation of swap space), so it has only 2GB and I did run with -j3. Actually there is swap on usb thumb drive for emergency use, but it jumps around (sdc, sdd etc.) so probably there really was no swap this time. 

File system is 82, I think, that would be journal 3 or something like that? Swap was 83 if I recall correctly or then other way around. I'm still linux noob, making progress everyday but some things are perfectly new to me. I hope to get to point where RoR works way it works with as well as it currently is possible, so that I can then work out some form of list what I had to do to make it that far, also I do this to two different 9.10 machines to get wider perspective, when process is complete there should be data (among lot of noise) to make more or less working list of what to do, that is at least the plan, which I just come up to. 

There seem to be temporarily malfunction in SVN tree, must try again later with this laptop and meanwhile get that other machine back to it's feet ;)

---

### Post by retro89 on 2010-04-23
I used the beta installer and it downloaded all the files to my home directory.When I click on the ror file it does nothing. What am I doing wrong?

---

### Post by jtbo on 2010-04-24
> **retro89 said:**
> I used the beta installer and it downloaded all the files to my home directory.When I click on the ror file it does nothing. What am I doing wrong?

Did you click one named rorconfig.sh ? If RoR has no config file it can't work. Also I don't know much about 32bit version with installer as I have 64bit and no installer.

---

### Post by retro89 on 2010-04-24
> **jtbo said:**
> Did you click one named rorconfig.sh ? If RoR has no config file it can't work. Also I don't know much about 32bit version with installer as I have 64bit and no installer.

I clicked on the rorconfig.sh and it did not launch the configuator.

---

### Post by jtbo on 2010-04-25
> **retro89 said:**
> I clicked on the rorconfig.sh and it did not launch the configuator.

I have to use terminal because I had to launch RoR.sh with sudo, otherwise it can't use rigsofrods dir in home dir. 

Try this, when you have dir where RoR is installed open, right click empty spot on that dir and choose open 'terminal here', then do sudo ./rorconfig.sh and hit enter, write your password and hit enter, does it work or is there error texts?

---

### Post by Aperion on 2010-04-25
> **jtbo said:**
> I have to use terminal because I had to launch RoR.sh with sudo, otherwise it can't use rigsofrods dir in home dir. 

Try this, when you have dir where RoR is installed open, right click empty spot on that dir and choose open 'terminal here', then do sudo ./rorconfig.sh and hit enter, write your password and hit enter, does it work or is there error texts?

you should not have to use sudo to run ror, if you do you might need to check your system settings.

But do run RoR from the console you can see any error messages that are printed, or you can post the RoR.log file.

---

### Post by jtbo on 2010-04-28
> **Aperion said:**
> you should not have to use sudo to run ror, if you do you might need to check your system settings.

But do run RoR from the console you can see any error messages that are printed, or you can post the RoR.log file.

0.36.3 does not work without sudo, 0.37.91 works without sudo, except it can't create log files to personal folders as it created those folders with such permissions that there is no right to write as normal user. If I chmod folders soon they are changed back. System settings being defaults.

Also I get more detailed messages when running RoR with sudo, it may of course blow my system, but then again I like living dangerously :P

---

### Post by Aperion on 2010-04-28
> **jtbo said:**
> 0.36.3 does not work without sudo, 0.37.91 works without sudo, except it can't create log files to personal folders as it created those folders with such permissions that there is no right to write as normal user. If I chmod folders soon they are changed back. System settings being defaults.

Also I get more detailed messages when running RoR with sudo, it may of course blow my system, but then again I like living dangerously :P
I've been playing RoR wince 0.29, and been deving for it since it went Open source, I have never once used sudo to run it, that's why I suggest checking out your settings, do you need to use sudo with any other games?

---

### Post by jtbo on 2010-04-29
> **Aperion said:**
> I've been playing RoR wince 0.29, and been deving for it since it went Open source, I have never once used sudo to run it, that's why I suggest checking out your settings, do you need to use sudo with any other games?

No, but then again, I don't game too much, there is always some program/command that needs it even it is quite rare. Don't know much from linux really, so haven't changed much of anything so that it does not go berserk. With RoR there has been lot of new stuff that had to be installed, first time doing such things, but those should not cause such behavior. 

Now I remember why I had to use sudo in first place, track selection did not show anything, not even when I did clear the cache, but with sudo it did start to work, it was related to rights to home dir, maybe this Xubuntu with Xwm has some protection in home dir, I don't know. 

wvdial needs sudo too, even I did read that it should not need it, but without sudo it does not find modem device at all. 

Maybe there is something like power user setting for profile, but haven't found anything like that, my user is just a user, there is not much to set it. 

Have to look into that some day, two straight days of migraine are starting to take it's toll so it is quite impossible to do any proper thinking at the moment.

---

### Post by Aperion on 2010-06-08
Just wanted to update that I am starting to publish some nightly builds to my personal website, they are located at [http://ror.chrisnem.com/nightlies/linux](http://ror.chrisnem.com/nightlies/linux) They are built on my home machine which runs 64bit Ubuntu 9.10 This assumes ones has all the dependencies in place. As for those I will try to get those published soon too.

Hopefully this will help in some small way.

edit:I uploaded all of my /usr/local/(lib|include) which is basically what is hopefully all the missing libs that RoR needs. Will continue to work on this and hopefully provide an easy to use dep file.

hehe forgot the link: [http://ror.chrisnem.com/linux-deps/RoR-x86_64-ubuntu-deps.tar.bz2](http://ror.chrisnem.com/linux-deps/RoR-x86_64-ubuntu-deps.tar.bz2)

edit2: the deps go into /usr/local

---

