---
title: "Bzflag broken in BB?"
date: 2005-10-13
forum: Gaming &amp; Leisure
---

### Post by Neeko on 2005-10-13
Hi,
I haven't been able to get Bzflag working at all in BB. 

This is the error I get (from a term window):
john@ubuntu:~$ bzflag
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  134 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x115
  Serial number of failed request:  122
  Current serial number in output stream:  124


Has anyone been able to get Bzflag working in B,Badger?

Thanks

---

### Post by Skye on 2005-10-13
The latest version of BZ works fine over here (Breezy Badger and Nvidia 6800 based system.)

I got the source for 2.0.4, ./configure 'd it, and then built the debian packages with checkinstall, and all works great.

What video drivers are you using?  What graphics card?

---

### Post by Ibuntu_52 on 2005-10-14
I have bzflag up and running.

Unfortunately the esd sound issue is still here, it's easily  solved by a killall esd.

I too compiled bzflag.If you need any help compiling please reply;)

---

### Post by Neeko on 2005-10-14
[QUOTE=Skye]
What video drivers are you using?  What graphics card?[/QUOTE]
Nvidia FX5200 AGP

john@ubuntu:~$ cat /proc/driver/nvidia/agp/status
Status:          Enabled
Driver:          AGPGART
AGP Rate:        8x
Fast Writes:     Disabled
SBA:             Enabled

Had this working fine in my other distro - only been using Ubuntu a couple of days now :p 

Where did you download the source from and what does checkinstall do?

Thanks

---

### Post by Skye on 2005-10-14
The BZFlag source is availible [url = http://ftp.bzflag.org/bzflag/bzflag-2.0.4.20050930.tar.bz2] here,[/url] and once you download it to your machine, you do the following.

```
sudo apt-get install checkinstall
```
This download the necessary checkinstall program from apt.

```
cd /wherever/you/saved/bzflag
./configure
```
Let that run, and install any libraries it needs but can't find- the output from ./configure should be fairly explicit in what it's missing.

Now, in the same directory as you ran ./configure, do 
```
checkinstall
```

This compiles the source and then creates a debain package from it, so that what you install can be easily managed by apt- it's much cleaner than just compiling things the normal way.  Let that run, follow th dialogue at the end to create the .deb package, and things *should* work.  Post your results back here.

---

### Post by Arktis on 2005-10-14
@[Skye]("member.php?u=9709") : Great tip, thanks!  I only wish I had known about checkinstall sooner.

---

### Post by nythacker on 2005-10-14
Hi,

Got BZFlag to work by typing this in the Terminal or Console window:

        [COLOR="Red"]bzflag -window[/COLOR]

Hope this helps!

Cheers!!! :KS

---

### Post by Neeko on 2005-10-14
Hmm, ./configure fails...

john@ubuntu:~/bzflag$ ./configure
BZFlag-2.0.4.20051014
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for whoami... yes
checking whether make sets $(MAKE)... (cached) yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking for ccache... no
checking for windres... :
checking whether ln -s works... yes
checking for ranlib... ranlib
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.

Looks like it can't find /lib/cpp to me. Any idea how I can install that lib - I tried synaptic but couldnt find it there?

Thx

---

### Post by Neeko on 2005-10-14
Ok, forget that last post...my bad....didnt have G++ installed.

However, I do have libcurl3 installed, but the ./configure script complains that I dont:

...
checking for curl >= 7.10.0... ./configure: line 19787: curl-config: command not found
FAILED
configure: WARNING: curl-config was not found
configure: error: libcurl is required. You must install it. See [http://curl.haxx.se/](http://curl.haxx.se/)
john@ubuntu:~/bzflag$ sudo apt-get install libcurl3
Reading package lists... Done
Building dependency tree... Done
libcurl3 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Do I need to create a symlink somewhere for this to work, or is this an incompatible version?

Thx

---

### Post by Skye on 2005-10-14
Anytime that you are compiling something and it claims you are missing a library, yet you think you have that library installed, make sure you have the library**-dev** package installed as well- the **-dev** packages are required to compile things from source, but they are not installed automatically.

IN your case, you're looking for the libcurl3-dev package.

---

### Post by Neeko on 2005-10-14
Yep, that was it thanks...

checkinstall produced this:

*****************************************
**** Debian package creation selected ***
*****************************************

Building Debian package...OK

Installing Debian package...OK

Erasing temporary files...OK

Writing backup package...OK

Deleting temp dir...OK


**********************************************************************

 Done. The new package has been installed and saved to
 /home/john/bzflag/bzflag_bzflag2.02-1_i386.deb

 You can remove it from your system anytime using:

      dpkg -r bzflag

**********************************************************************

john@ubuntu:~/bzflag$ 


Which looks good, but what do I do with it now ? (sorry if thats a stupid question I'm more familiar with rpms than dpkgs). I presume I now need to install the deb package somehow?

Thx

---

### Post by Skye on 2005-10-14
Nope, you should be all set.  The fact that it said 
```
 Done. The new package has been installed and saved to
/home/john/bzflag/bzflag_bzflag2.02-1_i386.deb
```
means it installed itself sucessfully, and can now be managed using apt or synaptic or your package manager of choice. 

Run the program by simplying typing in ```
bzflag
``` at a terminal, and the game should launch.

---

### Post by Neeko on 2005-10-15
I'm afraid not...

john@ubuntu:~$ bzflag
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  134 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x115
  Serial number of failed request:  122
  Current serial number in output stream:  124


This kind of looks like an X11 error to me. One thing I have noticed is that when I run glxgears, they turn very slowly and I dont get any FPS info.

NB I have updated from a preview release, should I download a new iso?

Any ideas?

Thx

---

### Post by Ibuntu_52 on 2005-10-15
to compile bzflag make sure you install all the sdl librarys, I forgot witch ones you need but just run a search in synaptic and download all the sdl packages with -dev on the end.

from the looks of it you need to download and install the nvidia drivers.I'm not sure exactly what you have to do to get them installed.

I haven't had a nvidia card for some time, but when I did I got it working simply by downloading the linux drivers from nvidia's website.This was in a different distro than ubuntu tho.

fortunately nvidia is pretty good about supporting linux.

also to get glxgears to display info in 5.10 you have to type

#glxgears -GLXGEARSISNOTABENCMARK (I think tha's it if not type #glxgears -help)

---

### Post by Arktis on 2005-10-15
>  john@ubuntu:~$ bzflag
 X Error of failed request:  BadValue (integer parameter out of range for operation)
   Major opcode of failed request:  134 (XFree86-VidModeExtension)
   Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
   Value in failed request:  0x115
   Serial number of failed request:  122
   Current serial number in output stream:  124

 I had the same problem about a month or so ago when "queen of maybe" came out, and purging the configs worked.

Your configuration files for bzflag are located in your home directory under the .bzf directory.  You'll have to turn on the showing of hidden files in nautilus in order to see it.  Once you do see it, remove it's entire contents and run bzflag again.

Should work. :D

---

### Post by Neeko on 2005-10-16
:( 
Nope.

I noticed SDL was required so I installed it, and the configure script said it had been included.

Oh, and I downloaded the current iso of 5.10 and reinstalled it, still no go with BzFlag.
I can get other OpenGL games working tho, from tuxkart to GLTron so I don't know where to look next...

john@ubuntu:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.3
...

Any ideas anyone?

Thx

---

### Post by Skye on 2005-10-16
Try running the game with the command:
```
bzflag -window -geometry 800x600+0+0
```
and post back here with the output.

---

### Post by Neeko on 2005-10-16
aye carumba!  :D 

Thank you so much!

It opens and plays fine in that window.  I guess that means I just need to change some settings within BzFlag to get it to play fullscreen.

---

### Post by Skye on 2005-10-16
Great!

The problem was, bzflag was not recognizing your screen resolution correctly.  Change the 800x600 part of the command to your current screen resolution (probably 1280x1024 or 1024x768) and it will take up the whole screen in a window.

---

