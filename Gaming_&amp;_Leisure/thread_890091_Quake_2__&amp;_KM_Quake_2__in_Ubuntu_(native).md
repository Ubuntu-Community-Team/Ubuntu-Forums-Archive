---
title: "Quake 2  &amp; KM Quake 2  in Ubuntu (native)"
date: 2008-08-14
forum: Gaming &amp; Leisure
---

### Post by PeterBBB on 2008-08-14
I had many problems getting native Quake2 to run in Ubuntu, and noticed from recent posts that several others were in difficulty too. Eventually I got it working. Like many things, its easy once you know how. The packages I used were not designed for Ubuntu. They were built for Debian & Fedora, and therefore a little tweaking is needed.

_Prerequisites_
You must have a Quake CD, or some source of the original games files. These are proprietary and not included in the downloads.

I'm running Ubuntu Hardy (64-bit) with Gnome on AMD64. What follows works for me on this system. To install deb & rpm packages you need first to install 'GDebi' and 'alien' respectively from the Ubuntu repositories via Synaptic (admin section) 

You must have an OpenGL / 3D setup. Check there is a file or symlink here by trying-

 ```
ls /usr/lib/libGL.so
```

If not, you need to sort this out before proceeding.

There are also 32bit versions of both games, but I have not tried them.


**_Installing Quake 2_**

Download the binary from
[http://packages.debian.org/sarge/amd64/quake2/download](http://packages.debian.org/sarge/amd64/quake2/download)

The file is called quake2_0.3-1.1_amd64.deb    This version of Quake has 4x3 resolutions up to 2048x1536 and wide-screen up to 1440x900

Double click on the .deb file you downloaded which opens the GDebi package manager and click on 'Install Package'.

Type quake2 from a terminal and answer y to the question. Quake will crash with 
> recursive shutdown
Error: Couldn't load pics/colormap.pcx] 
 
Copy the data files from the Quake CD with 
```
sudo cp -rv /media/Quake2/Install/Data/baseq2 /usr/lib/games/quake2

```
Try quake2 again. You will probably get a garbled window. Close it quickly as I found it can lock up the desktop.

To sort out the graphics type in a terminal

 ```
quake2 +set vid_ref glx
```

The graphics should be all right now, but probably no sound. Try

 ```
quake2 +set snddriver ao +set snddevice oss
```
 
Sound should now be working. 
 
To set up a launcher, right click on 'Applications', and select 'Edit Menus'. Add Quake 2 as a 'New Item' using the 'Command' string 

```
/usr/lib/games/quake2/quake2.real
```

The icon should appear and Quake2 should be all set to go. 
If you get mouse trouble, try switching to SDL graphics in game, exiting, then switch back to OpenGL GLX.


Now Quake 2 is working, its time to try **KM Quake**....  [http://kmq2.quakedev.com/screenshots.htm](http://kmq2.quakedev.com/screenshots.htm)
Don't download from this site. They are Windows only binaries!


**_Installing KM Quake 2_**

I found a Linux version on [ftp://brebs.me.uk/fedora/9/](ftp://brebs.me.uk/fedora/9/)
The file to download is

kmquake2-0.19.2-1.fc9.x86_64.rpm

This is a Fedora package. Convert it to Debian/Ubuntu with

```
alien km*.rpm
```

This will create the file kmquake2_0.19.2-2_amd64.deb

Install it using GDebi as before.

Copy the data files from the Quake CD with  
```
sudo cp -rv /media/Quake2/Install/Data/baseq2 /usr/lib64/kmquake
```

An Icon is created in the 'Applications' 'Games' menu, but I found the command needs editing for Ubuntu. Right click on Applications, navigate to Games  'KM Quake 2'. Right click on it and select properties. Change the command to just ```
kmquake2
```

Start KM Quake 2 from the icon and it should run, albeit in low resolution. This version does not have any wide-screen formats selectable within the game. If your screen resolution in not listed in the game's Video options then click on 'Places' 'Home Folder' and check 'View' 'Show Hidden Files'. Navigate to the .quake2/baseq2 folder and edit kmq2config.cfg  I was able to set up 1440x900 by changing the values as follows;
set gl_mode "-1"
set r_customheight "900"
set r_customwidth "1440"

Try the values for your screen here. Note, to bypass the intro video, space does not work. Hit [ESC] twice instead.

To get the most out of KM Quake you might like to download the high resolution graphics paks from 
[http://www-personal.umich.edu/~jimw/q2/](http://www-personal.umich.edu/~jimw/q2/)

Download
kmquake2_models.pk3
kmquake2_extras.pk3

Copy them to /usr/lib64/kmquake2/baseq2   You will need sudo privilege to do this. Use sudo cp .... or sudo nautilus etc.

To enable extra effects like shadows, flares, waves, they have to be enabled in kmq2config.cfg first.


Note; save games are all incompatible between different types of Quake2.  Quake2 & KM Quake 2 save games share the same folder and are incompatible, but KM Quake has extra save slots. If you are tired of disabling the Strogg Logistical train, you can start at any other point by starting the Quake console with ~  
Then an 'exec' command;
    
exec warehouse.cfg
exec jail.cfg
           	exec mine.cfg
        	exec factory.cfg
          	exec power.cfg
        	exec biggun.cfg
        	exec hangar.cfg
           	exec city.cfg
        	exec boss.cfg

[See original readme on the CD for more info on this]


Have fun!   Quake is a great game, and once installed, I've found these native versions rock solid.

Pete

---

### Post by Brebs on 2008-08-15
Binaries may not be very compatible between distros - the toolchains are different. What people should be doing is spending a bit of effort in [learning how to use](http://www.debian.org/doc/manuals/maint-guide/index.en.html) their distro's package manager. Really. It's important. Then grab my [kmquake2 .src.rpm](ftp://brebs.me.uk/fedora/9/) and recompile it. Heck, I could host it, but it needs somebody else who actually runs Ubuntu to create the package.

The reason for those changes, after using "alien", are because Fedora doesn't use separate "/games/" directories, and uses a little opengl checker (which is why you need to remove "-wrapper").

I see no reason to run "cp -rv /usr/lib/games/quake2 /usr/lib64/kmquake2" - it would only mess up the libs that kmquake2 uses, if anything. Do not copy libs from one program to another.

---

### Post by PeterBBB on 2008-08-20
Hi Paul, thanks for the comments. And many thanks for doing the Fedora port of KM Quake 2.

My original 'cp' didn't mess anything up, but didn't do what I intended anyway. Also I was under the mistaken impression that KM was a patch to Quake2 rather than a complete replacement. I've updated the original post to just cp the data files from the CD.

KM Quake2 is so much better that the original, so easy to install. If I had known all this at the start, I probably would not have bothered with the deb package of the original.

Your Fedora binaries are working fine in Ubuntu btw, the edit to the launcher only takes a few seconds. Seems to me any effort expended on compiling might be better spent on the latest version 0.2 Beta 3 which has the large maps enabled by default.

I noticed a few times that the game crashed after I got fragged. I realise now that is because I have games from other versions lying around, having noticed the comment in the source > *A single player death will automatically restore from the last save position.* and knowing that the game crashes on loading an incompatible file. Both give error "signal 15".

I suspect this crash is because of [http://bugs.gentoo.org/show_bug.cgi?id=140121#c23](http://bugs.gentoo.org/show_bug.cgi?id=140121#c23)
rather than a build issue. The patch is helpful for developers, but perhaps should best come out from release versions?


Discovered a file was missing for kquake2.  It can be downloaded from here, 

[http://qudos.quakedev.com/linux/quake2/engines/QuDos/QuDos-0.40.1.pk3](http://qudos.quakedev.com/linux/quake2/engines/QuDos/QuDos-0.40.1.pk3)

and placed in the baseq2 subdirectory. This .pk3 gets the menus working better. I was perhaps wrong in suggesting to start by editing km2config.cfg  The new features can be accessed via 'options -> effects' or 'video -> advanced options' from the ingame menu. KM Quake2 is flexible regarding .pk3 file names. It just loads whatever it finds.


How are people getting on with KM Quake 2 under Linux?  Over 100 have viewed the post, but only one has bothered to reply. Is it working fine? Problems? Still can't install? Too busy playing the game to comment?  Would be interesting to know...


Pete

---

### Post by Brebs on 2008-08-20
Hi PeterBBB,

> **PeterBBB said:**
> binaries are working fine in Ubuntu
That's good, but a bit of luck is involved. I do encourage people to package apps natively, because distros change things, and maybe break things which a native recompilation would fix ;)

> latest version 0.2 Beta 3
I took a look at [the latest kmquake2](http://kmq2.quakedev.com/), but the code has been greatly rearranged, and the Linux part of it is incomplete and broken. It would take someone with [QuDos](http://qudos.quakedev.com/)'s programming skills to get it working in Linux. I'll try to contact him - lost contact about a year ago.

> game crashes on loading an incompatible file.
Yeah, it's a bit silly for these (slightly incompatible) game engines to be sharing the *same* savegame slots.

> I suspect this crash is because of [http://bugs.gentoo.org/show_bug.cgi?id=140121#c23](http://bugs.gentoo.org/show_bug.cgi?id=140121#c23)
That patch fixes the tedious issue of savegames not loading after a recompilation, even if no code was changed.

An easy fix would be for kmquake2 to use ~/.kmquake2 rather than attempting to share ~/.quake2/baseq2/save/ with other incompatible quake2 engines.

> Discovered a file was missing for kmquake2... gets the menus working better.
That doesn't sound right. I'm including 2 .pk3 files for kmquake2 already:
```
$ rpm -ql kmquake2 | grep pk3
/usr/lib64/kmquake2/baseq2/flares.pk3
/usr/lib64/kmquake2/baseq2/kmquake2.pk3
```
What's missing from those 2 files?

> How are people getting on
It's a "niche market" ;)  As with [quake 1](http://www.quakeone.com/). Gaming in Linux is still second-place to Windows, [even for ID Software](http://www.linuxgames.com/archives/10532).

But yeah, it's nice to get feedback. Hint hint to everyone ;)

---

### Post by PeterBBB on 2008-08-20
> "It would take someone with QuDos's programming skills to get it working in Linux."

I don't claim to have much skill with C or Linux, but I've got it working here. I basically resolved all the build errors, sometimes with reference to your source (having built that first). Took me a day. Having built it, it seems to run OK, but I have not given it a full workout. 

Edit:* meant to say that by 'working', I just hacked the source to get it to build, and so far is has'nt fallen over. I suspect several recent linux patches are missing. If Qudos could be persuaded to look at the 0.2 source, that would be great*.

> "What's missing from those 2 files?"

Menu graphics* in QuDos-0.40.1 *. Just drop it in and see.  Its more important for 0.2, because there are streams of error messages if its missing.

I have 6 pk3 files now

flares
kmquake2
kmquake2_extras
kmquake2_levelshots_hi
kmquake2_models
QuDos-0.40.1

---

### Post by Brebs on 2008-09-06
> **PeterBBB said:**
> I've got it working here. I basically resolved all the build errors
Can you upload it [somewhere](http://www.google.co.uk/search?hl=en&as_q=file+upload&as_epq=&as_oq=&as_eq=&num=30&lr=lang_en&as_filetype=&ft=i&as_sitesearch=&as_qdr=all&as_rights=&as_occt=any&cr=&as_nlo=&as_nhi=&safe=off)? Would be interesting to take a look.

---

### Post by PeterBBB on 2008-09-11
Hi Brebs
It should now be available from

_[http://www.2shared.com/file/3912473/7b27fae8/kmquake2_src_020_beta3tar.html](http://www.2shared.com/file/3912473/7b27fae8/kmquake2_src_020_beta3tar.html)_

Let me know when you've got it, I'll remove it after a few days.

Please remember that this is rather a raw product. 'C' language and Makefiles are not really my thing (more Delphi if you were wondering), so if you find stuff that I have changed seems to make no sense, that's probably because it does make no sense at all! But please feel free to email me any queries on my changes.

The code had definitely forked BTW. Very few of the Gentoo linux fixes to 0.19 are in there.

I have messed around a little with difficulty level for skill level '1' in Combat & Weapons I think. You might want to take those changes back out. I was tempted myself, but I know if I start to polish this stuff, its just going to go on forever...



Pete

---

### Post by Brebs on 2008-09-11
Well done! It compiles and runs. I'll try to get it into a packageable state.

---

### Post by rajeev1204 on 2008-09-12
> **Brebs said:**
> Well done! It compiles and runs. I'll try to get it into a packageable state.

Iam getting this error when i try to run kmquake2.

rajeev@rajeev-desktop:~$ kmquake2
Using '/home/rajeev/.quake2/baseq2' for writing.
execing default.cfg
couldn't exec kmq2config.cfg
Console initialized.

------- sound initialization -------
Attempting to initialize OSS sound.
Initializing OSS Sound System
Stereo: ^91
Samples: ^932768
Samplepos: ^90
Samplebits: ^916
Submission_chunk: ^91
Speed: ^944100
Starting Ogg Vorbis.
OGG_LoadPlaylist: could not open playlist: No such file or directory.
No Ogg Vorbis files found.
------------------------------------

--------- Renderer Initialization ---------
ref_gl::R_Init() - could not load "libGL.so"
------------------------------------
CDAudio_Init: open of "/dev/cdrom" failed (2)
Segmentation fault

---

### Post by Crafty Kisses on 2008-09-12
Nice tutorial man, thanks!

---

### Post by PeterBBB on 2008-09-12
Looks like your real problem is this one

```
ref_gl::R_Init() - could not load "libGL.so"

```
Please note, I have only tried the 64bit version. 
Make sure your build did actually produce a libGL.so
I'm using a kmq2gamex86_64.so here.

From wherever you have put the kmquake2 executable, 
make sure your .so file is in a subdirectory called baseq2

---

### Post by Brebs on 2008-09-12
libGL.so is not provided by the game. You need to set up opengl properly for whatever video card you're using.

In Fedora 64-bit:
```
$ find /usr/lib64/ -name libGL.so
/usr/lib64/libGL.so

$ rpm -qf /usr/lib64/libGL.so
mesa-libGL-devel-7.1-0.37.fc9.x86_64
```

---

### Post by PeterBBB on 2008-09-12
Also, if you haven't installed the 0.19 .rpm binary first, you may have other unresolved library dependencies. You will need all of this lot to run from a source build...

libasound2 (>> 1.0.14), 
libc6 (>= 2.3), 
libgl1-mesa | libgl1, 
libgl1-mesa-glx | libgl1, 
libglu1-mesa | libglu1, 
libjpeg62, 
libogg0, 
libpng12-0 (>= 1.2.13-4), 
libvorbis0a (>= 1.2.0), 
libvorbisfile3 (>= 1.2.0), 
libx11-6, 
libxext6, 
libxxf86dga1, 
libxxf86vm1, 
zlib1g (>= 1:1.2.3.3.dfsg-1)



Pete

---

### Post by Uchiha_madara on 2008-09-12
i don't Know if Quake II is the Same of Quake Arena

I have installed Quake Arena and it Work's

---

### Post by rajeev1204 on 2008-09-12
> **PeterBBB said:**
> Looks like your real problem is this one

```
ref_gl::R_Init() - could not load "libGL.so"

```
Please note, I have only tried the 64bit version. 
Make sure your build did actually produce a libGL.so
I'm using a kmq2gamex86_64.so here.

From wherever you have put the kmquake2 executable, 
make sure your .so file is in a subdirectory called baseq2


Mine is a 64 bit hardy and i installed from the fedora 019 rpm.

there is a kmquake2.so in the baseq2 folder in /usr/lib64/kmquake2

---

### Post by PeterBBB on 2008-09-12
Hi Rajeev, Brebs is correct, the missing file is part of the graphics driver, not the game. 

On my system /usr/lib/libGL.so is a symlink which points to libGL.so.173.14.12
173 etc being the version number of the Nvidia driver in use.

Just a another thought. If you have somethink like /usr/lib/libGL.so.xxxxxxx
where xxxx could be anything, try creating a symlink to it (need sudo) and name the symlink as libGL.so
Also, a similar symlink named libGL.so.1 to the same library may be needed.


Pete

---

### Post by Brebs on 2008-09-12
No. Half-baked suggestions won't work. Follow the **proper** instructions for the video card, whatever it is. There are several files involved, and people creating symlinks without knowing what they're doing just get themselves into bigger messes :(

---

### Post by PeterBBB on 2008-09-12
I was afraid I had missed a critical step in the tutorial, but having rechecked the file dates it does look as though both my symlinks were created by the driver install (and so not by me). That said, a quick search with Google suggest that libGL.so is as slippery as the Pink Panther. ;-)

 ```
ls -l /usr/lib/libGl.so*
```

must I think list three files for (km)QuakeII to work. The driver library and the two symlinks that point to it. Something like this-


 /usr/lib/libGL.so   -> libGL.so.173.14.12
 /usr/lib/libGL.so.1 -> libGL.so.173.14.12
 /usr/lib/libGL.so.173.14.12

---

### Post by holr on 2008-09-24
Just wanted to say thank you for your guide. I have not only quake 2 running, but kmquake2 (something I had previously unheard of). Thanks!

---

### Post by DuGi on 2008-12-16
I just found this kmquake2 0.19.2 source -> [http://qudos.quakedev.com/linux/quake2/engines/KMQuake2/KMQuake2-SDL-0.19.2_src_unix.tar.bz2](http://qudos.quakedev.com/linux/quake2/engines/KMQuake2/KMQuake2-SDL-0.19.2_src_unix.tar.bz2)

it's compiling without problems on my system and working fine.

now i'm waiting for working 0.20 release...

---

### Post by ewg118 on 2008-12-20
Hi, thanks for the tutorial.  It has been difficult to find concise directions on how to get Q2 installed on a modern linux system.  I am having problems, however.  I've tried both directions for installing kmquake2 and using the debian package.  I'm going to focus more on trying to get kmquake2 installed though.

Okay, so I followed the directions in the original post for kmquake2, and what I get is this:

```
Using '/home/komet/.quake2/baseq2' for writing.
couldn't exec default.cfg
couldn't exec kmq2config.cfg
Console initialized.

------- sound initialization -------
Attempting to initialize OSS sound.
Initializing OSS Sound System
Stereo: ^91
Samples: ^932768
Samplepos: ^90
Samplebits: ^916
Submission_chunk: ^91
Speed: ^944100
Starting Ogg Vorbis.
OGG_LoadPlaylist: could not open playlist: No such file or directory.
No Ogg Vorbis files found.
------------------------------------

--------- Renderer Initialization ---------
recursive shutdown
Error: Couldn't load pics/colormap.pcx
```

I have put baseq2 into /usr/lib64/kmquake2 .  Is this incorrect?  Where should I put baseq2?

Thanks.

---

### Post by Brebs on 2008-12-20
Run:

strace -e trace=file whateveryourexecutableis

And you can see for yourself where it is looking.

pics/colormap.pcx is actually in pak0.pak, which should be in /usr/share/whatever rather than /usr/lib/whatever.

And don't forget file ownership/permissions, so that your user can actually read the files.

---

### Post by ewg118 on 2008-12-20
Thanks.  It was a permissions issue.  kmquake2 is quite beautiful.  It cleans up Quake 2 without losing that authentic feel that the opengl gave it.

---

### Post by PeterBBB on 2008-12-21
> **DuGi said:**
>  now i'm waiting for working 0.20 release...

I've uploaded it again.

[http://www.2shared.com/file/4498266/302fc561/kmquake2_src_020_beta3tar.html]("http://www.2shared.com/file/4498266/302fc561/kmquake2_src_020_beta3tar.html")

---

### Post by SparcMan on 2009-03-23
I'm using Ubuntu 8.10 x64 and I got the regular Quake 2 engine to work, but not kmquake2.
After some Trial and Error, here are basically the steps that seemed to work for me:

Installed the quake2-data package (sorry, don't remember from where, you'll have to google it)

ran the command: ```
sudo dpkg-reconfigure quake2-data
```
That copied the files off the game CD to the correct location.

Then I installed (or reinstalled in my case) quake2_0.3-1.1_amd64.deb

After running it with quake2 +set vid_ref glx
it worked great.

One mistake I made was adding a GL package with GLlib.so that replaced the one that was already installed (but doesn't have a GLlib.so) and it messed up all by 3D graphics in the OS.
That's the main reason I cant get kmquake to work - it's looking for GLlib.so and the GL package I'm using doesn't have one.

The video driver I/m using is the ATI/AMD proprietary FGLRX

---

